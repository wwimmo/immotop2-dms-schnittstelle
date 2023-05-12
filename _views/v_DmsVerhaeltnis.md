# v_DmsVerhaeltnis

View über alle Verhältnisse.

## Tabellendefinition

| Name                 | Kommentar                            | Datentyp | Länge | Nullable |
| :------------------- | :----------------------------------- | :------- | ----: | :------: |
| s_seqnr              | Der Primärschlüssel                  | long     |    64 |    N     |
| gueltigvon           | Verhältnisbeginn                     | date     |       |    N     |
| gueltigbis           | Verhältnisende                       | date     |       |    J     |
| objekt_seqnr         | Primärschlüssel des Objekts          | long     |    64 |    N     |
| objekt_nr            | Nummer des Objekts                   | int      |    32 |    N     |
| liegenschaft_seqnr   | Primärschüssel der Liegenschaft      | long     |    64 |    N     |
| liegenschaft_nr      | Nummer der Liegenschaft              | int      |    32 |    N     |
| mandant_seqnr        | Primärschlüssel des Mandanten        | long     |    64 |    N     |
| mandant_nr           | Nummer des Mandanten                 | int      |    32 |    N     |
| verhaeltnisstatus_nr |                                      | Int      |    32 |          |
| mieter_seqnr         |                                      | Long     |    64 |          |
| mieter_nr            |                                      | Int      |    32 |          |
| mandanttyp_rolle     | Mieter, Eigentümer                   | nvarchar |   100 |    N     |
| mandanttyp_code      | V, G, S                              | nvarchar |    10 |    N     |
| insts                | Insert Timestamp (Ab Version 2.6.32) | date     |       |    N     |
| updts                | Update Timestamp (Ab Version 2.6.32) | date     |       |    N     |
