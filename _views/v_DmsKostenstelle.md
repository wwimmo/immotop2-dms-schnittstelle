# v_DmsKostenstelle

Alle Informationen zur Kostenstelle.

## Tabellendefinition

| Name                                 | Kommentar                                                   | Datentyp | Länge | Nullable |
| :----------------------------------- | :---------------------------------------------------------- | :------- | ----: | :------: |
| Bez                                  | Die Bezeichnung                                             | varchar  |   100 |    N     |
| s_seqnr                              | Der Primärschlüssel                                         | long     |    64 |    N     |
| kostenstelletypnr                    | 1 = lg, 2 = lggruppe, 3 = weder lg noch lggruppe            | int      |    32 |    N     |
| kuerzel                              |                                                             | varchar  |       |    J     |
| mandant_seqnr                        |                                                             | long     |    64 |    N     |
| reihenfolge                          |                                                             | int      |    32 |    N     |
| liegenschaft_seqnr                   | (kostenstelle_seqnr von lg oder null)                       | long     |    64 |    J     |
| liegenschaftgruppe-nebenkosten_seqnr | typ 1: kostenstelle_seqnr via lg                            |          |       |          |
|                                      | typ 2: via liegenschaftgruppenk (nötig für abrechn periode) |          |       |          |
|                                      | Typ 3: leer, da nicht zuweisbar                             | long     |    64 |    J     |
| mitarbeiter1                         | MA zur LG oder ersten LG                                    | varchar  |       |    J     |
| mitarbeiter2                         | MA zur LG oder ersten LG                                    | varchar  |       |    J     |
| bewiteam1                            | LG oder ersten LG                                           | varchar  |       |    J     |
| bewiteam2                            | LG oder ersten LG                                           | varchar  |       |    J     |
| plz                                  |                                                             | varchar  |       |    J     |
| ort                                  |                                                             | varchar  |       |    J     |
| strasse                              |                                                             | varchar  |       |    J     |
| land                                 | schweiz                                                     | varchar  |    20 |    J     |
| kanton                               | zh                                                          | varchar  |     2 |    J     |
| insts                                | Insert Timestamp (Ab Version 2.6.32)                        | date     |       |    N     |
| updts                                | Update Timestamp (Ab Version 2.6.32)                        | date     |       |    N     |
