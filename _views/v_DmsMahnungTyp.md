# v_DmsMahnungTyp

In dieser View sind die Mahnungstypen definiert.

## Tabellendefinition

| Name                        | Kommentar                                     | Datentyp | Länge | Nullable |
| :-------------------------- | :-------------------------------------------- | :------- | ----: | :------: |
| bez                         | Die Bezeichnung                               | varchar  |   100 |    N     |
| s_seqnr                     | Der Primärschlüssel                           | bigint   |    64 |    N     |
| kuerzel                     | Kuerzel                                       | varchar  |   100 |    N     |
| verwendungvermietung        | Wird beim Vermietungsmandanten verwendet.     | smallint |    16 |    N     |
| verwendunggenossenschaft    | Wird beim Genossenschaftsmandanten verwendet. | smallint |    16 |    N     |
| verwendungstockwerkeigentum | Wird beim STWEG-Mandanten verwendet.          | smallint |    16 |    N     |
| insts                       | Insert Timestamp (Ab Version 2.6.32)          | date     |       |    N     |
| updts                       | Update Timestamp (Ab Version 2.6.32)          | date     |       |    N     |
