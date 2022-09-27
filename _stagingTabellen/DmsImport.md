# DmsImport

Dies ist die Haupttabelle für den Import von Dokumenten. Hier werden Informationen zum Dokument und dem Archiv abgespeichert.

## Tabellendefinition

| Name                      | Kommentar                                                                                                                                                | Datentyp              | Null-able | Defaultwert |
| :------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------- | :-------- | :---------- |
| dmsarchiveguid            | Id des Dms-Archivs. Falls das Dms mit verschiedenen Archiven arbeitet, so hat jedes eine eigene Guid; falls nicht, kann der Defaultwert gelassen werden. | uniqueidentifier (32) | N         | newid()     |
| dmsdocumentguid           | Guid, respektive Identifikations-String des Dokuments gemäss den Systemeinträgen des Dms; dieses Feld ist nur relevant, wenn die dmsdocumentid 0 ist.    | varchar(100)          | N         | ‘’          |
| dmsdocumentid             | Id des Dokuments gemäss den Systemeinträgen des Dms.                                                                                                     | long                  | N         | 0           |
| dmsdateiname              | Name des Dokuments (Ab Version 2.6.10)                                                                                                                   | filename              | N         |             |
| dmsimportfehlercode_seqnr | Wird von ImmoTop2 abgefüllt. Die mögliche Werte stehen in der Datenbank-View v_DmsImportFehlerCode.                                                      | key                   | J         |             |
| dmsimportstatus_seqr      | Die mögliche Werte stehen in der Datenbank-View v_DmsImportStatus.                                                                                       | key                   | N         | 0           |
| dmsinsts                  | Zeitpunkt der Erfassung im Dms als Zeitstempel.                                                                                                          | timestamp             | N         | getdate()   |
| dmsinsusr                 | Benutzer, der das Dokument im Dms importiert hat.                                                                                                        | varchar(20)           | N         | ‘’          |
| dmsupdatets               | Zeitpunkt der Bearbeitung im Dms als Zeitstempel.                                                                                                        | timestamp             | N         | getdate()   |
| dmsupdateusr              | Benutzer, der den Datensatz im Dms bearbeitet hat.                                                                                                       | varchar(20)           | N         | ‘’          |
