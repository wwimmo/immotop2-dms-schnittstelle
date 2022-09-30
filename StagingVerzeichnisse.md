# Schnittstelle Staging-Verzeichnisse
Analog zu den Staging-Tabellen in der ImmoTop2-Datenbank können Staging-Verzeichnisse für die Kommunikation zwischen ImmoTop2 und dem DMS genutzt werden.
Es werden zwei Staging-Verzeichnisse benötigt:
- Stagingverzeichnis1: Commands und Dokumente von ImmoTop2 an das DMS
- Stagingverzeichnis2: Commands und Dokumente vom DMS an ImmoTop2

In diese Staging-Verzeichnisse werden Steuerdateien und Dokumente geschrieben

## Namengebung der Dateien
Die eindeutigen Namen des Dokumentes und der Steuerdatei müssen sich entsprechen. 
Die Namen der beiden Dateien unterscheiden sich nur im Filesuffix. 
Das Dokument selber hat den Namen «UniqueDokumentID.suffix».

Damit auch XML-Dateien zwischen den beiden Software-Systemen ausgetauscht werden können, hat die Steuerdatei den proprietären FileSuffix «xml_it2».

## Steuerdatei
Die Steuerdatei enthält Metadaten eines Dokuments und Anweisungen. Sie:
- hat XML-Format
- wird erst nach dem Dokument in das Stagingverzeichnis geschrieben

### Struktur
| Name des XML-Elements    | Werte         | Bemerkungen                                                                                                                                                                                                           |
| :----------------------- | :------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Version                  | 1.0           | Ermöglicht zukünftige Erweiterungen/Modifikationen der Steuerdatei  |
| Action                   | NewDocument   | NeueDatei                                                     |
|                          | SavedDocument | Datei wurde im DMS gespeichert, das DMS liefert die ID des Dokumentes                                                                                |

ReplaceDokument wird nicht implementiert, es wird DeleteDocument/NewDocument benutzt

### Beispiele für Steuerdateien

#### Ein ImmoTop2-Benutzer will ein neues Dokument ins DMS laden:
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


