# v_DmsVorsteuerAnteil

Definitionen der Vorsteueranteile.

## Tabellendefinition

| Name               | Kommentar                            | Datentyp | Länge | Nullable |
| :----------------- | :----------------------------------- | :------- | ----: | :------: |
| mandant_seqnr      |                                      | long     |    64 |    N     |
| kostenstelle_seqnr | Null, falls mand                     | long     |    64 |    N     |
| kostengruppe_seqnr |                                      | long     |    64 |    J     |
| gueltigvon         |                                      | date     |       |    N     |
| gueltigbis         |                                      | date     |       |    J     |
| wert               | Wert in %                            | decimal  |       |    N     |
| insts              | Insert Timestamp (Ab Version 2.6.32) | date     |       |    N     |
| updts              | Update Timestamp (Ab Version 2.6.32) | date     |       |    N     |
