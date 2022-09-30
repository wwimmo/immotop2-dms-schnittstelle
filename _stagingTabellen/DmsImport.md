# DmsImport

Dies ist die Haupttabelle für den Import von Dokumenten. Hier werden Informationen zum Dokument und dem Archiv abgespeichert.

## Tabellendefinition

| Name                      | Kommentar                                                                                                                                                | Datentyp              | Null-able | Defaultwert |
| :------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------- | :-------- | :---------- |
| dmsarchiveguid            | Eindeutige Id des Dms-Archivs. Falls das Dms mit verschiedenen Archiven arbeitet, so hat jedes eine eigene Guid | uniqueidentifier (32) | N         | newid()     |
| dmsdocumentguid           | Eindeutige Identifikations des Dokuments.<br>Dokumente werden von ImmoTop2 im DMS anhand dieses Attributes gesucht<br><br>Dieses Feld hat folgende Struktur:<br>1) Textkonstante "WW"<br>2) "0" (Versionsnummer)<br>3) GUID ohne Bindestriche (in C#: Guid.NewGuid().ToString("N"))    | varchar(100)          | N         | ‘’          |
| dmsdocumentid             | Numerische eindeutige Id des Dokuments.<br>Numerische IDs können bei unterschiedlichen Zulieferern heikel sein, deshalb wird "dmsdocumentguid" als Suchattribut bevorzugt<br>Falls "dmsdocumentguid" keinen gültigen Wert hat, werden Dokumente im DMS anhand dieses Attributs gesucht<br>Dieses Attribut existiert primär, um die Rückwärtskompatibilität mit ImmoTop zu gewährleisten                                                                                                     | long                  | N         | 0           |
| dmsdateiname              | Name des Dokuments (Ab Version 2.6.10)                                                                                                                   | filename              | N         |             |
| dmsimportfehlercode_seqnr | Wird von ImmoTop2 abgefüllt. Die mögliche Werte stehen in der Datenbank-View v_DmsImportFehlerCode.                                                      | key                   | J         |             |
| dmsimportstatus_seqr      | Die mögliche Werte stehen in der Datenbank-View v_DmsImportStatus.                                                                                       | key                   | N         | 0           |
| dmsinsts                  | Zeitpunkt der Erfassung im Dms als Zeitstempel.                                                                                                          | timestamp             | N         | getdate()   |
| dmsinsusr                 | Benutzer, der das Dokument im Dms importiert hat.                                                                                                        | varchar(20)           | N         | ‘’          |
| dmsupdatets               | Zeitpunkt der Bearbeitung im Dms als Zeitstempel.                                                                                                        | timestamp             | N         | getdate()   |
| dmsupdateusr              | Benutzer, der den Datensatz im Dms bearbeitet hat.                                                                                                       | varchar(20)           | N         | ‘’          |
