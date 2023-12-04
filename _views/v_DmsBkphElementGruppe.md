# v_DmsBkphElementGruppe

View über die BKP-H-Elementengruppe.

## Tabellendefinition

| Name                | Kommentar           | Datentyp | Länge | Nullable |
| :------------------ | :------------------ | :------- | ----: | :------: |
| s_seqnr             | Der Primärschlüssel | long     |    64 |    N     |
| nr                  | Nummer              | int      |    32 |    N     |
| bez                 | Bezeichnung         | nvarchar |   100 |    N     |
| code                | Code des Elementes  | nvarchar |    10 |    N     |
| bkphhauptgruppe     | Haupptgruppe        | nvarchar |   100 |    N     |
| bkphhauptgruppenr   | Haupptgruppenummer  | int      |    32 |    N     |
| bkphhauptgruppecode | Haupptgruppe        | nvarchar |    10 |    N     |
