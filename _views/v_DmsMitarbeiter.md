# v_DmsMitarbeiter

View über alle Mitarbeiter.

## Tabellendefinition

| Name       | Kommentar                         | Datentyp | Länge | Nullable |
| :--------- | :-------------------------------- | :------- | ----: | :------: |
| s_seqnr    | Primärschlüssel des Mitarbeiters. | long     |    64 |    N     |
| nr         | Die Nummer des Mitarbeiters.      | int      |    32 |    N     |
| vorname    |                                   | nvarchar |   100 |    J     |
| name       |                                   | nvarchar |   100 |    J     |
| festnetz   |                                   | nvarchar |    20 |    J     |
| mobile     |                                   | nvarchar |    20 |    J     |
| fax        |                                   | nvarchar |    20 |    J     |
| email      |                                   | nvarchar |   100 |    J     |
| geschlecht |                                   | nvarchar |   100 |    J     |
