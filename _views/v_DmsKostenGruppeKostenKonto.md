# v_DmsKostenGruppeKostenKonto

Für Vorsteueranteil zum Kostenkonto. Falls keine Vorsteueranteil in der Staging-Tabelle mitgegeben wird, wird der Vorsteueranteil beim Import ermittelt.

## Tabellendefinition

| Name               | Kommentar                                         | Datentyp | Länge | Nullable |
| :----------------- | :------------------------------------------------ | :------- | ----: | :------: |
| mandant_seqnr      |                                                   | long     |    64 |    N     |
| kostenkonto_seqnr  | Entspricht der konto_seqnr                        | long     |    64 |    N     |
| kostengruppe_seqnr |                                                   | long     |    64 |    J     |
| gueltigvon         | Von kostengruppemandant bzw. kostengruppelggruppe | date     |       |    N     |
| gueltigbis         |                                                   | date     |       |    J     |
| prioritaet         | 1 = hoch (lggruppe), 2 = tief                     |          |       |          |
