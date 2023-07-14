# v_DmsMandant

In dieser View werden die Informationen des Mandanten angezeigt.

## Tabellendefinition

| Name                    | Kommentar                                         | Datentyp | Länge | Nullable |
| :---------------------- | :------------------------------------------------ | :------- | ----: | :------: |
| bez                     | Die Bezeichnung                                   | varchar  |   100 |    N     |
| nr                      | Nummer des Eintrags                               | int      |    32 |    N     |
| s_seqnr                 | Der Primärschlüssel                               | key      |    64 |    N     |
| mandanttypcode          | V = Vermietung, S = Stockwerk, G = Genossenschaft | varchar  |     1 |    N     |
| person_seqnr            | Primärschlüssel der Person                        | key      |    64 |    N     |
| person_nr               | Nummer der Person                                 | int      |    32 |    N     |
| name1                   | Nachname                                          | varchar  |    60 |    N     |
| name2                   | Vorname                                           | varchar  |    60 |    N     |
| strasse                 |                                                   | varchar  |    67 |    J     |
| Plz                     |                                                   | varchar  |    15 |    N     |
| postfach                |                                                   | varchar  |    60 |    N     |
| ort                     |                                                   | varchar  |    60 |    N     |
| land                    |                                                   | varchar  |    10 |    J     |
| istmwstpflichtig        | *                                                 | smallint |    16 |    J     |
| defaultzahlstelle_seqnr |                                                   | key      |    64 |    J     |
| gueltigvon              |                                                   | date     |       |    N     |
| gueltigbis              |                                                   | date     |       |    J     |
| insts                   | Insert Timestamp (Ab Version 2.6.32)              | date     |       |    N     |
| updts                   | Update Timestamp (Ab Version 2.6.32)              | date     |       |    N     |

- defaultzahlstelle_seqnr ab Version 2.6.36 verfügbar
