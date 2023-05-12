# v_DmsObjekt

View über alle Objekte.

## Tabellendefinition

| Name               | Kommentar                            | Datentyp | Länge | Nullable |
| :----------------- | :----------------------------------- | :------- | ----: | :------: |
| s_seqnr            | Der Primärschlüssel                  | long     |    64 |    N     |
| nr                 | Nummer des Objekts                   | int      |    32 |    N     |
| bez                | Bezeichnung des Objekts              | nvarchar |   100 |    N     |
| liegenschaft_seqnr | Primärschüssel der Liegenschaft      | long     |    64 |    N     |
| liegenschaft_nr    | Nummer der Liegenschaft              | int      |    32 |    N     |
| mandant_seqnr      | Primärschlüssel des Mandanten        | long     |    64 |    N     |
| mandant_nr         | Nummer des Mandanten                 | int      |    32 |    N     |
| insts              | Insert Timestamp (Ab Version 2.6.32) | date     |       |    N     |
| updts              | Update Timestamp (Ab Version 2.6.32) | date     |       |    N     |
