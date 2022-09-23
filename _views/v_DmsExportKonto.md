# v_DmsExportKonto

ImmoTop hatte für jedes Konto max. ein Exportkonto. In ImmoTop2 kann ein Konto je nach Exportziel verschiedene Exportkonten zugewiesen haben.

## Tabellendefinition

| Name                            | Kommentar                             | Datentyp | Länge | Nullable |
| :------------------------------ | :------------------------------------ | :------- | ----: | :------: |
| konto_seqnr                     | Primärschlüssel des Kontos            | long     |    64 |    N     |
| zielkonto                       | Nummer des Zielkontos                 | nvarchar |   100 |    J     |
| buchungexportzieldefinition_bez | Bezeichnung der Exportziel-Definition | nvarchar |   100 |    J     |
| buchungexportzielformat_bez     | Bezeichnung des Exportziel-Formats    | nvarchar |   100 |    J     |
