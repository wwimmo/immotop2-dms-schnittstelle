# v_DmsBelegzahlungAngaben

View über alle Belegzahlungsangaben.

## Tabellendefinition

| Name                                 | Kommentar                                       | Datentyp | Länge | Nullable |
| :----------------------------------- | :---------------------------------------------- | :------- | ----: | :------: |
| mandant_seqnr                        | Primärschlüssel des Mandanten.                  | long     |    64 |    N     |
| mandantnr                            | Nummer des Mandanten.                           | int      |    32 |    N     |
| beleg_seqnr                          | Primärschlüssel des Beleges.                    | long     |   100 |    N     |
| belegnr                              | Nummer des Beleges.                             | int      |   100 |    N     |
| belegdatum                           | Datum des Beleges.                              | date     |    20 |    N     |
| anzahlzahlungposten                  | Anzahl der Zahlungsposten.                      | int      |    20 |    N     |
| belegart_seqnr                       | Primärschlüssel der Belegart.                   | long     |    20 |    N     |
| belegartnr                           | Nummder der Belegart.                           | int      |   100 |    N     |
| zahlungsliste_seqnr                  | Primärschlüssel der Zahlungsliste.              | long     |   100 |    J     |
| zahlungslistenr                      | Nummer der Zahlungsliste.                       | int      |    32 |    J     |
| valutaoderverrechnetdatum            | Valutadatum oder Verrechnetdatum.               | date     |       |    J     |
| istvollstaendigbezahltoderverrechnet | Gibt an ob vollständig bezahlt oder verrechnet. | smallint |    16 |    N     |
| totalzahlungbetrag                   | Der Totale Betrag aller Zahlungen des Beleges   | decimal  |  12,2 |    N     |
| dmsimport_seqnr                      | Primärschlüssel des DmsImports.                 | long     |    64 |    J     |
| dmsarchiveguid                       | Die GUID des DmsArchivs.                        | uid      |       |    J     |
| dmsdocumentid                        | Die Dokumenten ID aus dem DMS.                  | long     |    64 |    J     |
| dmskreditorbelegbelegnummer          | Die Belegnummer aus dem DMS.                    | int      |    32 |    J     |
