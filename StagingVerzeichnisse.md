# Dokumenten-Schnittstelle via Staging-Verzeichnisse
Über diese Schnittstelle werden Dokumente zwischen dem DMS und ImmoTop2 verschoben (zB Benutzer speichert aus ImmoTop2 ein neues Dokument im externen DMS, Benutzer löscht ein Dokument im externen DMS,....).</br>
Die Staging-Verzeichnisse werden als einheitliche Lowtech-Schnittstelle für die Kommunikation zwischen ImmoTop2 und verschiedenen DMS-Produkten genutzt.
Es werden zwei Staging-Verzeichnisse benötigt:
- Stagingverzeichnis1: Steuerdateien und evtl. Dokumente von ImmoTop2 an das DMS
- Stagingverzeichnis2: Steuerdateien und evtl. Dokumente vom DMS an ImmoTop2

<img src="./_images/dmsarchiv.png" alt="Wo werden Archive konfiguriert?" style="float:left; margin-right:10px;" /><br><br>
<img src="./_images/ConfigStagingverzeichnisse.png" alt="Stagingverzeichnisse in ImmoTop2 konfigurieren" style="float:left; margin-right:10px;" />

## Steuerdatei
Die Steuerdatei enthält Metadaten eines Dokuments und Steuer-Anweisungen. Sie:
- hat XML-Format
- wird erst nach dem Dokument in das Stagingverzeichnis geschrieben
  (verhindert, dass XML-Dateien ohne passende Daten-Datei verarbeitet werden)
- soll zuerst vollständig in ein temporäres Verzeichnis geschrieben und erst dann ins Staging-Verzeichnis "gemoved" werden
  (verhindert, dass ImmoTop2 unvollständig geschriebene XML-Dateien verarbeitet)

### Namengebung der Steuerdateien
Die eindeutigen Namen des Dokumentes und der Steuerdatei müssen sich entsprechen, dh. Namen der beiden Dateien unterscheiden sich nur im Filesuffix. 
Damit auch XML-Dateien zwischen den beiden Software-Systemen ausgetauscht werden können, hat die XML-Steuerdatei den proprietären FileSuffix «.xml_it2».

Möglicher Inhalt eines Stagingverzeichnisses:<br>
<img src="./_images/Stagingverzeichnis.png" alt="Möglicher Inhalt eines Stagingverzeichnisses" style="float:left; margin-right:10px;" />

### Struktur einer Steuerdatei
| Name des XML-Elements    | Werte           | Bemerkungen  |
| :----------------------- | :------------   | :--------------------------------------------   |
| Version                  | 1.0             | Ermöglicht zukünftige Erweiterungen/Modifikationen der Steuerdatei  |
| Action                   | NewDocument     | Neues Dokument im DMS speichern  |
|                          | SavedDocument   | Datei wurde im DMS gespeichert, das DMS liefert Infos des gespeicherten Dokumentes zurück an ImmoTop2. |
|                          | GetDocumenInfos | Falls "SavedDocument" verloren ging oder..., kann ImmoTop2 die Infos zu einem Dokument erneut anfordern |
|                          | DownloadDocument| ImmoTop2 will eine Datei aus dem DMS runterladen (siehe UseCase 8) |
|                          | DeleteDocument  | Datei im DMS löschen (siehe UseCase 3)|
|                          | ReplaceDocument | Wird nicht implementiert, es muss DeleteDocument/NewDocument benutzt werden.<br>Damit ist die Dokumentensynchronisation mit dem Portal einfach möglich. |
| DmsArchivId              | Text            | Wird nur bei DMS benötigt, die innerhalb einer Instanz mehrere Archive erlauben.<br>Eindeutige ID des Archivs, in dem das Dokument gespeichert wird<br>Dient dem ArchivMapping beim Kreditoren-Workflow.  |
| DmsDocumentId            | Text            | Eindeutige ID eines Dokuments im DMS<br>Wird immoTop2 mitgeteilt mit der Steuerdatei vom Typ "SavedDocument"<br>Sie wird für die Visualisierung der Dokumente via DMS-DocumentViewer oder "DownloadDocument" benötigt.  |
| DocumentId               | Text            | Eindeutige ID eines Dokuments in ImmoTop2<br>Primärschlüssel des Dokuments, der für die REST- oder Datenbankschnittstelle benutzt werden kann.  |
| DateiName                | Text            | Sprechender Dateiname   |
| ClientName               | Text            | Name des PC, auf dem der ImmoTop2-Client läuft (wird für "DownloadDocument" benötigt -> UseCase8)    |
| FehlerText               | Text            | Falls es bei der Verabeitung im DMS ein Problem gab (zB Dokument existiert nicht mehr)   |

### Beispiele von Steuerdateien

#### Beispiel 1: Ein ImmoTop2-Benutzer will ein neues Dokument im DMS speichern:
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

#### Beispiel 2: Das DMS liefert ImmoTop2 Informationen zu einem neu im DMS gespeicherten Dokument:
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
## UseCase 1: ImmoTop2 will ein Dokument ins DMS schreiben
ImmoTop2 kennt Dokumentarten (Bilanz, Erfolgsrechnung, ....).
Für jede Dokumentart:
- ist festgelegt, welche Indexwerte optional/mandatory beim Speichern eines Dokumentes gesetzt werden müssen.
- kann der Benutzer via Checkbox "Ablage DMS" konfigurieren, ob Dokumente in internen oder einem externen Archiv gespeichert werden sollen.

Ein Kunde kann mehrere externe DMS-Archive zB in verschiedenen Versionen nutzen.<br>
Genau eines der externen Archive muss als "Standardarchiv" konfiguriert sein, damit ImmoTop2 weiss, wohin ein neues Dokument geschrieben werden soll.
Bereits gespeicherte Dokumente bleiben dort, wo sie initial gespeichert wurden.

Ablauf:
- ImmoTop2 schreibt einen Verweis-Datensatz in die ImmoTop2-Datenbank auf das externe Archiv, in dem Dokument gespeichert werden soll
- ImmoTop2 schreibt dann eine Steuerdatei mit Action "NewDocument" in den Stagingfolder1 und liefert dabei den Primärschlüssel des Dokuments (XML-Element "DocumentId")
- Danach schreibt ImmoTop2 das Dokument in den Stagingfolder1
- Das DMS erkennt die Steuerdatei und schreibt das Dokument ins  DMS-Archiv
- Das DMS löscht danach sowohl die Steuerdatei als auch das Dokument im Stagingfolder1
- Nun liefert das DMS im StagingFolder2 eine Steuerdatei mit Action "SavedDocument"<br>Diese Steuerdatei enthält die ID des Dokumentes (Element "DmsDocumentId"), die für das Löschen bzw. die Visualisierung eines Dokuments via DMS-Documentviewer benötigt wird 
- ImmoTop2 verarbeitet diese Steuerdatei (aktualisiert den Verweis-Datensatz im internen Archiv) und löscht dann die Steuerdatei in StagingFolder2

## UseCase 2: ImmoTop2-Benutzer will ein Dokument sehen, das im DMS gespeichert ist
ImmoTop2 weiss, dass das vom Benutzer verlangte Dokument in einem externen Archiv gespeichert ist und baut den URL für den DMS-Documentviewer anhand des für das Archiv hinterlegten URL.
Die im URL des Archivs hinterlegten Platzhalter «%DocId%» und «%ArchivId%» werden durch die effektiven DocId bzw ArchivId ersetzt (gilt nicht für das DMS Docuware).
Danach wird der Standardbrowser gestartet und das Dokument über den DMS-DocumentViewer im Browser geöffnet.<br>
Der im Browser gestartete DMS-Documentviewer ermöglicht dann den Download, das Drucken,... eines Dokumentes. 

## UseCase 3: ImmoTop2 löscht ein Dokument im externen DMS
Ein Benutzer hat sich entschieden, ein Dokument zu löschen.
ImmoTop2 weiss anhand der Konfigurationsdaten, dass das zu löschende Dokument in einem externen Archiv gespeichert ist.

Ablauf:
- ImmoTop2 schreibt eine Steuerdatei mit Action "DeleteDocument" in den Stagingfolder1
- ImmoTop2 löscht den Verweis auf das Dokument in seiner Datenbank
- Das DMS löscht das Dokument im Archiv anhand des XML-Elementes "DmsDocumentId"
- Das DMS löscht die Steuerdatei im Stagingfolder1

## UseCase 4: Re-Synchronisieren von ImmoTop2-Indexwerten im  externen DMS
Nur notwendig, wenn das DMS neben der ImmoTop2-DocId zusätzlich auch noch weitere ImmoTop2-Indexwerte (=Dokument-Metadaten) in numerischer und/oder in Textform benutzt (zB Name eines Mandanten). Es ist möglich, das Indexwerte in ImmoTop2 ändern (zB Namensänderung eines Mieters).<br>
<b>Deshalb müssen ImmoTop2-Indexwerte im externen DMS periodisch mit ImmoTop2 re-synchronisiert werden</b> (ImmoTop2 ist der Master der ImmoTop2-Indexwerte).

ImmoTop2 liefert beim Schreiben eines Dokumentes den Primärschlüssel (XML-Element "DocumentId").
Anhand dieses Primärschlüssels kann das DMS weitere Indexwerte eines Dokumentes anhand der View "[v_DmsDokumentIndexFelder](_views/v_DmsDokumentIndexFelder.md)" oder des [REST-Service](RestService.md) "GetDmsDokumentIndexFelderByDmsDocumentId" lesen.<b>
Für praktisch alle DB-Views existieren als Alternative auch ImmoTop2-REST-Services</b>.

Sollten diese Indexwerte nicht alle gewünschten Daten enthalten, können mit weiteren REST-Services oder DB-Views zusätzliche Daten aus ImmoTop2 gelesen werden.
So liefert zB die View "v_DmsMandant" den Namen, den Typ,... des Mandanten.

## UseCase 5: ImmoTop2 verlinkt Dokumente, die im externen DMS gespeichert wurden (erst für den Kreditoren-Workflow implementiert)
Dokumente, die bereits im DMS gespeichert sind, sollen in ImmoTop2 integriert werden.<br>Das Dokument bleibt im externen DMS gespeichert. In immoTop2 werden nur die Indexwerte und eine Verlinkung auf das extern gespeciherte Dokument geschrieben.

Bemerkung: Dieser Usecase wurde nur für Kreditorenbelege via Kreditoren-Workflow bereits realisiert.
Für alle weiteren Dokumentarten muss ein analoger Ablauf neu programmiert werden.<br>

Weil ImmoTop2 der Master für die Indexwerte ist und relativ komplexe Regeln für die Dokumenten-Indexierung hat,<br> 
müssen beim Laden auch eines extern gespeicherten Dokumentes die Indexwerte anhand der ImmoTop2-Regeln gesetzt werden.<br>
Diese Indexierung muss für beliebige Dokumentarten deshalb manuell in ImmoTop2 gemacht werden, damit die Indexierungsregeln konsistent angewandt bleiben.

Ablauf:
- Das DMS schreibt eine Steuerdatei in Stagingfolder2
- ImmoTop2-Benutzer erfahren von diesen Dokumenten und starten dann die manuelle Indexierung

<img src="./_images/UseCase5.png" alt="UseCase2" style="float:left; margin-right:10px;" />

## UseCase 6: Dokumente werden aus ImmoTop2 ins externe DMS verschoben (noch nicht implementiert)
Das DMS will Dokumente aus dem internen ImmoTop2-Archiv übernehmen (ImmoTop2-Export), dh das Dokument wird verschoben.<br>
Dieser UseCase wird (noch) nicht benötigt. 

## UseCase 7: Dokumente werden aus dem externen DMS nach ImmoTop2 verschoben (noch nicht implementiert)
ImmoTop2 will Dokumente aus dem externen DMS-Archiv übernehmen (ImmoTop2-Import), dh das Dokument wird verschoben.<br>
Dieser UseCase wird (noch) nicht benötigt. 

Bemerkung: In UseCase5 bleibt das Dokument im externen DMS gespeichert

## UseCase 8: ImmoTop2 downloaded Dokumente aus dem externen DMS (neu seit Januar 2024)
ImmoTop2 downloaded Dokumente aus dem externen DMS-Archiv, dh das Dokument bleibt im externen DMS gespeichert.<br>
Konkreter UseCase: Buchhaltungsbelege werden für die Revision exportiert.<br>
<br>
Herausforderungen:<br>
- Bei diesem UseCase müssen die vom DMS gelieferten Daten dem Client und nicht dem Server geliefert werden, denn die exportierte Datei muss schlussendlich in ein Export-Verzeichnis geschrieben werden, das auf dem ImmoTop2-Client sichtbar sein muss<br>
- Um die vom DMS gelieferte Datei nicht auf dem Server zwischenzuparkieren und über einen neuen Transportmechanismus zwischen Client und Server runtergeladen werden muss, schreibt das DMS die Antwort direkt in den StagingFolder1<br>
- Damit bei einer Mehrplatzinstallation die DMS-Antworten nicht konkurrenzierend verarbeitet werden, erhält jeder Client ein eigenes Subverzeichnis im StagingFolder1 mit dem Namen des Client und dem Namen des Windows-Benutzers (relevant bei Terminalserver-Installationen)<br>
<br><br>
Ablauf:
- Der ImmoTop2-Client stellt sicher, dass im StagingFolder1 ein Sub-Verzeichnis mit dem Namen der "Client-Workstation+Windows-Benutzer" existiert<br>
- Der ImmoTop2-Client schreibt wie bei allen anderen UseCase eine Steuerdatei (Typ "DownloadDocument") in den StagingFolder1<br>Geliefert werden die XML-Attribute DmsArchivId, DmsDocumentId, DateiName und ClientName.<br>
- das externe DMS liest diese Steuerdatei und schreibt die verlangte Datei im StagingFolder1 mit einem eindeutigen Namen in das Subverzeichnis der "Workstation+Benutzer"  (der Name des Subverzeichnisses befindet sich in den von ImmoTop2 gelieferten XML-Metadaten)<br>
- danach schreibt das externe DMS eine Steuerdatei ebenfalls vom Typ "DownloadDocument" in dasselbe Subverzeichnis des StagingFolder1<br>Geliefert werden muss nur das XML-Attribut "DateiName"
- falls im DMS ein Verarbeitungsfehler auftritt (zB Datei wurde gelöscht), wird der Fehler benutzerverständlich ins XML-Attribut "Fehlertext" geschrieben<br>
- der ImmoTop2-Client entdeckt diese Steuerdatei im Workstation-Folder des StagingFolder1 über einen FileListener und schreibt die Datei mit dem NAmen "DAteiName" direkt ins Exportverzeichnis<br>




