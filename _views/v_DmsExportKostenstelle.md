# v_DmsExportKostenstelle

ImmoTop hatte für jede Kostenstelle max. eine Exportkostenstelle. In ImmoTop2 kann eine Kostenstelle je nach Export-ziel verschiedene Exportkostenstellen zugewiesen haben.

## Tabellendefinition

| Name                            | Kommentar                             | Datentyp | Länge | Nullable |
| :------------------------------ | :------------------------------------ | :------- | ----: | :------: |
| kostenstelle_seqnr              | Primärschlüssel der Kostenstelle      | long     |    64 |    N     |
| zielkostenstelle                | Nummer der Zielkostenstelle           | nvarchar |   100 |    J     |
| buchungexportzieldefinition_bez | Bezeichnung der Exportziel-Definition | nvarchar |   100 |    J     |
| buchungexportzielformat_bez     | Bezeichnung des Exportziel-Formats    | nvarchar |   100 |    J     |
