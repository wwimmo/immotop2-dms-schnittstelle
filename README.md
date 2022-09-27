# immotop2-dms-schnittstelle

Offene DMS Schnittstelle für das Immobilien-ERP ImmoTop2

Dieses Dokument richtet sich an DMS Hersteller und Implementationspartner. Es enthält die Dokumentation über den Aufbau und Inhalt der universellen DMS Schnittstelle ImmoTop2. Das Dokument dient als Implementationshilfe und Nachschlagewerk für DMS Hersteller und Implementationspartner.

## Zusammenspiel Dms mit ImmoTop2

ImmoTop2 stellt Stammdaten dem Dms in Views zur Verfügung.

Das Dms erhält einen Benutzer für lesenden Zugriff. Die Verbindung auf die Views erfolgt mittels ODBC, zusätzlich denkbar wäre auch eine Verbindung mittels ADO.Net, OLE.DB. Ein REST WebService steht auch zur Verügung.

Der Beleg wird im Dms gescannt.

Der Beleg durchläuft im Dms einen Kreditoren-Workflow.

Metainformationen zum Beleg werden vom Dms in ImmoTop2 geschrieben. Hierfür hat das Dms Schreibrechte auf ausgewählte Dms-Tabellen vom ImmoTop2, sogenannte Staging-Tabellen.

In ImmoTop2 wird der Beleg geprüft. Die Daten werden gegebenenfalls ergänzt oder korrigiert und in die Buchhaltung geschrieben.

Die Rechnung wird über ImmoTop2 ausbezahlt.

## ImmoTop2 Views

Die nachfolgenden Views dienen der Workflow Engine des Dms dazu, die zulässigen Datenkombinationen zu ermitteln. Fragen, die beantwortet werden, sind: 

- Existiert der Kreditor bereits?
- Wie ist der Kontenrahmen des Mandanten?
- Welche Kostenstellen passen zum gewählten Konto?
- Soll mit Mwst gebucht werden oder nicht?
- Etc.

| View                                                           | Details                                                     |
| :------------------------------------------------------------- | :---------------------------------------------------------- |
| [v_DmsImportFehlerCode](./_views/v_DmsImportFehlerCode.md)     | View mit den Fehlercodes für das Importieren von Dokumenten |
| [v_DmsImportStatus](./_views/v_DmsImportStatus.md)             | Status der Importierten von Dokumente                       |
| [v_DmsMandant](./_views/v_DmsMandant.md)                       | Information zu den Mandanten                                |
| [v_DmsMandantZahlstelle](./_views/v_DmsMandantZahlstelle.md)   | Infromation zur Zahlstelle des Mandanten                    |
| [v_DmsKreditor](./_views/v_DmsKreditor.md)                     | Informationen zu den Kreditoren                             |
| [v_DmsKreditorZahlstelle](./_views/v_DmsKreditorZahlstelle.md) | Zahlstellen der Kreditoren                                  |
| [v_DmsKonto](./_views/v_DmsKonto.md)                           | Kontenoplan                                                 |
