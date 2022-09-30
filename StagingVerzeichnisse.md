# Schnittstelle Staging-Verzeichnisse
Analog zu den Staging-Tabellen in der ImmoTop2-Datenbank können Staging-Verzeichnisse für die Kommunikation zwischen ImmoTop2 und dem DMS genutzt werden.
Es werden zwei Staging-Verzeichnisse benötigt:
- Stagingverzeichnis1: Commands und Dokumente von ImmoTop2 an das DMS
- Stagingverzeichnis2: Commands und Dokumente vom DMS an ImmoTop2

In diese Staging-Verzeichnisse werden Steuerdateien und Dokumente geschrieben.
In ImmoTop2 werden sie konfiguriert unter Schnittstellen/ DMS-Archiv:
<img src="./_images/ConfigStagingVerzeichnisse" alt="Stagingverzeichnisse in ImmoTop2 konfigurieren" style="float:left; margin-right:10px;" />


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


ReplaceDokument wird nicht implementiert, es wird DeleteDocument/NewDocument benutzt

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


