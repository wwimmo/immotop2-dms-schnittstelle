# Schnittstelle Staging-Verzeichnisse
Analog zu den Staging-Tabellen in der ImmoTop2-Datenbank können Staging-Verzeichnisse für die Kommunikation zwischen ImmoTop2 und dem DMS genutzt werden.
Es werden zwei Staging-Verzeichnisse benötigt:
- Stagingverzeichnis1: Commands und Dokumente von ImmoTop2 an das DMS
- Stagingverzeichnis2: Commands und Dokumente vom DMS an ImmoTop2

In diese Staging-Verzeichnisse werden Steuerdateien und Dokumente geschrieben.
In ImmoTop2 werden sie konfiguriert unter Schnittstellen/ DMS-Archiv:
<img src="./_images/ConfigStagingverzeichnisse.png" alt="Stagingverzeichnisse in ImmoTop2 konfigurieren" style="float:left; margin-right:10px;" />


## Namengebung der Dateien in den Stagingverzeichnissen
Die eindeutigen Namen des Dokumentes und der Steuerdatei müssen sich entsprechen. 
Die Namen der beiden Dateien unterscheiden sich nur im Filesuffix. 
Das Dokument selber hat den Namen «UniqueDokumentID.suffix».

Damit auch XML-Dateien zwischen den beiden Software-Systemen ausgetauscht werden können, hat die Steuerdatei den proprietären FileSuffix «xml_it2».

## Steuerdatei
Die Steuerdatei enthält Metadaten eines Dokuments und Anweisungen. Sie:
- hat XML-Format
- wird erst nach dem Dokument in das Stagingverzeichnis geschrieben

### Struktur
| Name des XML-Elements    | Werte           | Bemerkungen  |
| :----------------------- | :------------   | :--------------------------------------------   |
| Version                  | 1.0             | Ermöglicht zukünftige Erweiterungen/Modifikationen der Steuerdatei  |
| Action                   | NewDocument     | Neues Dokument im DMS speichern  |
|                          | SavedDocument   | Datei wurde im DMS gespeichert, das DMS liefert Infos des gespiecherten Dokumentes |
|                          | DeleteDocument  | Datei im DMS löschen |
|                          | ReplaceDocument | Wird nicht implementiert, es muss DeleteDocument/NewDocument benutzt werden<br>Damit ist eine einfache Dokumentensynchronisation mit dem Portal  möglich |
| DmsArchivId              | Text            | Eindeutige ID des Archivs, in dem das Doku-ment gespeichert wird<br>(primär relevant, wenn mehrere Archive installiert sind, die denselben BasisURL haben)  |
| DmsDocumentId            | Text            | Eindeutige ID eines Dokuments im DMS<br>Wird für die Visualisierung der Dokumente via DMS-DocumentViewer benötigt  |
| DocumentId               | Text            | Eindeutige ID eines Dokuments in ImmoTop2  (Primärschlüssel des Dokuments, der für die REST- oder Datenabnkschnittstelle benutzt werden kann)  |
| DateiName                | Text            | Sprechender Dateiname   |


Möglicher Inhalt eines Stagingverzeichnisses:
<img src="./_images/Stagingverzeichnis.png" alt="Möglicher Inhalt eines Stagingverzeichnisses" style="float:left; margin-right:10px;" />

### Beispiele für Steuerdateien

#### Ein ImmoTop2-Benutzer will ein neues Dokument im DMS speichern:
 ```
 <?xml version="1.0" encoding="utf-8"?>
<ControlFile>
<Action>NewDocument</Action>
<DmsArchivId>Archiv1</DmsArchivId>
<DmsDocumentId />
<DocumentId>117</DocumentId>
<DateiName>qrcode.bmp</DateiName>
</ControlFile>
```

#### Das DMS teilt ImmoTop2 Informationen zum gespeicherten Dokument mit
```
<?xml version="1.0" encoding="utf-8"?>
<ControlFile>
<Action>SavedDocument</Action>
<DmsArchivId>Archiv1</DmsArchivId>
<DmsDocumentId>1234</DmsDocumentId>
<DocumentId>117</DocumentId>
<DateiName>qrcode.bmp</DateiName>
</ControlFile>
```

# Use Cases
## UseCase1: ImmoTop2 will ein Dokument ins DMS schreiben
ImmoTop2 kennt Dokumentarten (Bilanz, Erfolgsrechnung, ....).
Für jede Dokumentart ist individuell definiert, welche Indexwerte optiona/mandatory beim Speichern eines Dokumentes gesetzt werden müssen.
Für jede Dokumentart kann der Benutzer konfigurieren, wo Dokumente einer bestimmten Dokumentart gespeichert werden (internes oder externes Archiv).
Wenn für eine Dokumentart die Checkbox "Ablage DMS" aktiviert wurde, dann werden alle Dokumente dieser Dokumentart im externen Standardarchiv gespeichert.
Es darf bei den DMS-Archiven genau eines der externen Archive als "Standardarchiv" konfiguriert sein.

Ablauf:
- ImmoTop2 schreibt einen Verweis-Datensatz ins interne Archiv, der die Adressdaten des extern gespeicherten Dokuments enthält
- ImmoTop2 schreibt eine Steuerdatei mit Action "NewDocument" in den Stagingfolder1 und liefert dabei den Primärschlüssel des Dokuments (XML-Element "DocumentId")
- Danach schreibt ImmoTop2 das Dokument in den Stagingfolder1
- Das DMS erkennt die Steuerdatei und schreibt das Dokument ins Archiv
- Das DMS löscht danach sowohl die Steuerdatei als auch das Dokument im Stagingfolder1
- Nun liefert das DMS im StagingFolder2 eine Steuerdatei mit Action "SavedDocument"<br>Diese Steuerdatei enthält die ID des Dokumentes, die für das Löschen bzw. die Visualisierung eines Dokuments via DMS-Documentviewer benötigt wird 
- ImmoTop2 verarbeitet diese Steuerdatei (aktualisiert den Verweis-Datensatz im internen Archiv) und löscht dann die Steuerdatei in StagingFolder2

## UseCase2: Benutzer will Dokument sehen, das im DMS gespeichert ist
ImmoTop2 sieht, dass das vom Benutzer angeforderte Dokument in einem externen Archiv espeichert ist und baut den URL für den DMS-Documentviewer anhand des für das Archiv hinterlegten URL.
Die im URL hinterlegten Platzhalter «%DocId%» in «%ArchivId%» werden durch die effektiven DocId bzw ArchivId ersetzt.
Danach wird der Standardbrowser gestartet und das Dokument über den DMS-DocumentViewer im Browser geöffnet.

## UseCase3: ImmoTop2 will ein Dokument im DMS löschen
Ein Benutzer hat sich entscheiden, ein Dokument zu löschen.
ImmoTop2 sieht anhand der Konfigurationsdaten, dass das Dokument in einem externen Archiv gespeichert ist

Ablauf:
- ImmoTop2 schreibt eine Steuerdatei mit Action "DeleteDocument" in den Stagingfolder1
- ImmoTop2 löscht den Verweis auf das Dokument in seiner Datenbank
- Das DMS löscht das Dokument im Archiv
- Das DMS löscht die Steuerdatei im Stagingfolder1


## UseCase4: Das DMS liest die ImmoTop2-Indexwerte eines Dokumentes
Wird benötigt, wenn, wenn das DMS neben der ImmoTop2-DocId zusätzlich auch noch die Indexwerte in numerischer und/oder in Textform benötigt (zB Name eines Mandanten). 
Das Synchronisieren der Indexwerte muss im externen DMS periodisch ausgeführt werden, denn Indexwerte können in ImmoTop2 jederzeit geändert werden (zB Name einer Liegenschaft)

ImmoTop2 liefert beim Schreiben eines Dokumentes den Primärschlüssel (XML-Element "DocumentId").
Anhand dieses Primärschlüssels kann das DMS weitere Indexwerte eines Dokumentes anhand der View "v_DmsDokument" lesen.
Sollten diese Indexwerte nicht alle gewünschten Daten enthalten, können mit weiteren Views zusätzliche Daten aus ImmoTop2 gelesen werden.

So liefert zB die View v_DmsMandant den Namen, den Typ,… des Mandanten.
<b>Für die meisten Views existieren als Alternative auch ImmoTop2-REST-Services</b>.


## UseCase5: DMS schreibt Dokumente nach ImmoTop2 (noch nicht implementiert)
Bemerkung: Dieser Usecase kann für Kreditorenbelege auch via Kreditoren-Workflow realisiert werden.

Das DMS schreibt eine Steuerdatei in Stagingfolder2, das vom ImmoTop2-Server-Prozess überwacht wird.
Weil ImmoTop2 der Master für die Indexwerte ist, müssen beim Import des Dokumentes die Indexwerte anhand der Regeln in ImmoTop2 korrekt gesetzt werden.
Diese Indexierung muss deshalb manuell gemacht werden.

<img src="./_images/UseCase5.png" alt="UseCase2" style="float:left; margin-right:10px;" />


## UseCase6: DMS liest Dokumente aus ImmoTop2 (noch nicht implementiert)
Das DMS will Dokumente lesen, die zwar im internen Archiv von ImmoTop2, aber nicht im DMS gespeichert sind.
Dieser UseCase wird (noch) nicht benötigt. 



