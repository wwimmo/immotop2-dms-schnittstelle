# v_DmsAnlageTechnisch

View über alle technische Anlagen.

## Tabellendefinition

| Name                    | Kommentar                               | Datentyp | Länge | Nullable |
| :---------------------- | :-------------------------------------- | :------- | ----: | :------: |
| s_seqnr                 | Der Primärschlüssel                     | long     |    64 |    N     |
| nr                      | Nummer                                  | int      |    32 |    N     |
| bez                     | Bezeichnung                             | nvarchar |   100 |    N     |
| mandant_seqnr           | Primärschlüssel des Mandanten           | long     |    64 |    N     |
| liegenschaft_seqnr      | Primärschüssel der Liegenschaft         | long     |    64 |    J     |
| objekt_seqnr            | Primärschlüssel des Objektes            | long     |    64 |    J     |
| bkphelementgruppe_seqnr | Primärschlüssel der BKP-H-Elementgruppe | long     |    64 |    J     |
| insts                   | Insert Timestamp                        | date     |       |    N     |
| updts                   | Update Timestamp                        | date     |       |    N     |
