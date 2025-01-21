# v_DmsMieter

View über alle Mieter.

## Tabellendefinition

| Name          | Kommentar                                             | Datentyp | Länge | Nullable |
| :------------ | :---------------------------------------------------- | :------- | ----: | :------: |
| s_seqnr       | Der Primärschlüssel                                   | long     |    64 |    N     |
| nr            | Nummer des Mieters                                    | int      |    32 |    N     |
| bez           | Bezeichnung des Mieters                               | nvarchar |   100 |    N     |
| mandant_seqnr | Primärschlüssel des Mandanten                         | long     |    64 |    N     |
| mandant_nr    | Nummer des Mandanten                                  | int      |    32 |    N     |
| IstAktiv      | Gibt an, ob der Mieter aktiv ist. (Ab Version 2.7.19) | smallint |    16 |    N     |
| insts         | Insert Timestamp (Ab Version 2.6.32)                  | date     |       |    N     |
| updts         | Update Timestamp (Ab Version 2.6.32)                  | date     |       |    N     |
