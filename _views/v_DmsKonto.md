# v_DmsKonto

In dieser View wird der Kontoplan zum Mandanten angezeigt. Konten, die eine Kostenstelle verlangen, sind mit istkostenstellepflicht markiert. Welche Kostenstellen zulässig sind und ob gewisse Zusatzfelder zu Pflichtfelder werden, regelt der Nebenbuchtyp. Beispielsweise muss bei einem DmsBelegPosten, der auf ein Debitorkonto verweist, zwingend ein Mahntyp mitgegeben werden.

## Tabellendefinition

| Name                    | Kommentar                                                            | Datentyp | Länge | Nullable |
| :---------------------- | :------------------------------------------------------------------- | :------- | ----: | :------: |
| bez                     | Die Bezeichnung                                                      | varchar  |   100 |    N     |
| mandant_seqnr           | Der Mandant.                                                         | bigint   |    64 |    N     |
| s_seqnr                 | Der Primärschlüssel                                                  | long     |    64 |    N     |
| kontonr                 |                                                                      | varchar  |    20 |    N     |
| stufe                   | Unklar, GB klärt ab                                                  | smallint |    16 |    N     |
| nebenbuchtypnr          | 1 = Kostenbuch, 2 = Debitorenbuch, 3 = Kapitalbuch, NULL = Hauptbuch | int      |    32 |    N     |
| istkostenstellepflicht  | Gibt an, ob die Angabe einer Kostenstelle nötig ist.                 | smallint |    16 |    N     |
| Istmengepflicht         | Gibt an, ob die Angabe einer Menge nötig ist.                        | smallint |    16 |    N     |
| einheit                 | Falls mit Mengenangaben gearbeitet wird                              | char     |    20 |    J     |
| mengeAngabe             | z.B. 100 Liter                                                       | varchar  |    20 |    J     |
| mwstcode_seqnr          |                                                                      | long     |    64 |    J     |
| mitmwstbindung          |                                                                      | smallint |    16 |    N     |
| kontengruppesoll_seqnr  | Primärschlüssel Abschlussposition bei Soll-Saldo                     | long     |    64 |    J     |
| kontengruppesoll_nr     | Nummer der Abschlussposition bei Soll-Saldo                          | varchar  |    20 |    J     |
| kontengruppehaben_seqnr | Primärschlüssel Abschlussposition bei Haben-Saldo                    | long     |    64 |    J     |
| kontengruppehaben_nr    | Nummer der Abschlussposition bei Haben-Saldo                         | varchar  |    20 |    J     |
| code                    | Konsolidierungscode (nur bei Hauptbuchkonten)                        | nvarchar |   100 |    J     |
| insts                   | Insert Timestamp (Ab Version 2.6.32)                                 | date     |       |    N     |
| updts                   | Update Timestamp (Ab Version 2.6.32)                                 | date     |       |    N     |
