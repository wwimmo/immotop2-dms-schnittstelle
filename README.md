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
