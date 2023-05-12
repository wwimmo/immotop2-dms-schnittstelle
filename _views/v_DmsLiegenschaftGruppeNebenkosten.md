# v_DmsLiegenschaftGruppeNebenkosten

View über alle Liegnschaftengruppenebenkosten.

## Tabellendefinition

| Name               | Kommentar                                       | Datentyp | Länge | Nullable |
| :----------------- | :---------------------------------------------- | :------- | ----: | :------: |
| s_seqnr            | Der Primärschlüssel                             | long     |    64 |    N     |
| nr                 | Nummer der Liegenschaftengruppe NK              | int      |    32 |    N     |
| bez                | Bezeichung der Liegenschaftengruppe NK          | nvarchar |   100 |    N     |
| mandant_seqnr      | Primärschlüssel des Mandanten                   | long     |    64 |    N     |
| mandant_nr         | Nummer des Mandanten                            | int      |    32 |    N     |
| kostenstelle_seqnr | Primärschlüssel der dazugehörigen Kosten-stelle | long     |    64 |    J     |
| insts              | Insert Timestamp (Ab Version 2.6.32)            | date     |       |    N     |
| updts              | Update Timestamp (Ab Version 2.6.32)            | date     |       |    N     |
