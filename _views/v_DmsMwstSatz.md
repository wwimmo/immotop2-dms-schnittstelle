# v_DmsMwstSatz

Der jeweilige Satz der zu einem definierten Zeitraum zu einem MwstCode gehört.

## Tabellendefinition

| Name           | Kommentar                            | Datentyp | Länge | Nullable |
| :------------- | :----------------------------------- | :------- | ----: | :------: |
| mwstsatz_seqnr |                                      | long     |    64 |    N     |
| bez            | Bezeichnung des Mwst                 | varchar  |   100 |    N     |
| gueltigvon     |                                      | Date     |       |    N     |
| gueltigbis     |                                      | Date     |       |    J     |
| wert           |                                      | decimal  |       |    N     |
| insts          | Insert Timestamp (Ab Version 2.6.32) | date     |       |    N     |
| updts          | Update Timestamp (Ab Version 2.6.32) | date     |       |    N     |
