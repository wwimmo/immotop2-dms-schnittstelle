# v_DmsMwstCode

Kein gueltigVon, solange nicht Wert gebraucht wird.

## Tabellendefinition

| Name            | Kommentar                                                                                     | Datentyp | Länge | Nullable |
| :-------------- | :-------------------------------------------------------------------------------------------- | :------- | ----: | :------: |
| istvstmutierbar |                                                                                               | smallint |    16 |    N     |
| kuerzel         | Nur Info ob reduziert oder nicht. Der eigentliche Prozentsatz wird erst beim Buchen ermittelt | varchar  |   100 |    N     |
| mandant_seqnr   |                                                                                               | long     |    64 |    N     |
| s_seqnr         | Der Primärschlüssel                                                                           | long     |    64 |    N     |
| mwstsatz_seqnr  | Fremdschlüssel zum MwstSatz                                                                   | long     |    64 |    N     |
| insts           | Insert Timestamp (Ab Version 2.6.32)                                                          | date     |       |    N     |
| updts           | Update Timestamp (Ab Version 2.6.32)                                                          | date     |       |    N     |
