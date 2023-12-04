# v_DmsGeraetTyp

View über die Geraetetypen.

## Tabellendefinition

| Name              | Kommentar                           | Datentyp | Länge | Nullable |
| :---------------- | :---------------------------------- | :------- | ----: | :------: |
| s_seqnr           | Der Primärschlüssel                 | long     |    64 |    N     |
| bez               | Bezeichnung                         | nvarchar |   100 |    N     |
| kennung           | Kennung des Typs                    | nvarchar |   100 |    N     |
| bkphelement_seqnr | Primärschlüssel des BKP-H-Elementes | long     |    64 |    J     |
