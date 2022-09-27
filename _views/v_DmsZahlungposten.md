# v_DmsZahlungposten

View über alle Zahlungsposten.

## Tabellendefinition

| Name                                   | Kommentar                                       | Datentyp | Länge | Nullable |
| :------------------------------------- | :---------------------------------------------- | :------- | ----: | :------: |
| beleg_seqnr                            | Primärschlüssel des Beleges                     | long     |    64 |    N     |
| belegnr                                | Nummer des Beleges                              | int      |    32 |    N     |
| mandant_seqnr                          | Primärschlüssel des Mandanten                   | long     |    64 |    N     |
| mandantnr                              | Nummer des Mandanten                            | int      |    32 |    N     |
| belegzahlung_seqnr                     | Primärschlüssel der Belegzahlung                | long     |    64 |    J     |
| belegzahlungnr                         | Nummer der Belegzahlung                         | int      |    32 |    J     |
| belegart_seqnr                         | Primärschlüssel der Belegart                    | long     |    64 |    N     |
| belegartnr                             | Nummer der Belegart                             | int      |    32 |    N     |
| zahlungsliste_seqnr                    | Primärschlüssel der Zahlungsliste               | long     |    64 |    J     |
| zahlungslistenr                        | Nummer der Zahlungsliste                        | int      |    32 |    J     |
| zahlungslistestatus_seqnr              | Primärschlüssel des Status der Zahlungsliste    | long     |    64 |    J     |
| zahlungslistestatusnr                  | Nummer des Status                               | int      |    32 |    J     |
| zahlungslistestatusbez                 | Bezeichnung des Status                          | nvarchar |   100 |    J     |
| valutadatum                            | Valutadatum                                     | date     |       |    J     |
| istverrechnet                          | Gibt an ob Beleg verrechnet wurde               | smallint |    16 |    N     |
| istaufzahlunglisteoderverrechnet       | Gibt an ob auf Zahlungsliste oder verrechnet    | smallint |    16 |    N     |
| istbezahltoderverrechnet               | Gibt an ob bezahlt oder verrechnet              | smallint |    16 |    N     |
| zahlunglistevalutaoderverrechnetdatum  | Valutadatum oder Verrechnetdatum                | date     |       |    J     |
| zahlunglisteerstelloderverrechnetdatum | Erstell- oder Verrechnetdatum der Zahlungsliste | Date     |       |    J     |
| betragzahlung                          | Betrag                                          | decimal  |  12,2 |    J     |
