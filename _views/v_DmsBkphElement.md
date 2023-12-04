# v_DmsBkphElement

View über die BKP-H-Elemente.

## Tabellendefinition

| Name                    | Kommentar                               | Datentyp | Länge | Nullable |
| :---------------------- | :-------------------------------------- | :------- | ----: | :------: |
| s_seqnr                 | Der Primärschlüssel                     | long     |    64 |    N     |
| nr                      | Nummer                                  | int      |    32 |    N     |
| bez                     | Bezeichnung                             | nvarchar |   100 |    N     |
| code                    | Code des Elementes                      | nvarchar |    10 |    N     |
| bkphelementgruppe_seqnr | Primärschlüssel der BKP-H-Elementgruppe | long     |    64 |    N     |
