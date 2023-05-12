# v_DmsKreditorZahlstelle

In dieser View werden die Zahlstellen der Kreditoren angezeigt.

## Tabellendefinition

| Name                 | Kommentar                               | Datentyp | Länge | Nullable |
| :------------------- | :-------------------------------------- | :------- | ----: | :------: |
| bez                  | Die Bezeichnung                         | varchar  |   100 |    N     |
| s_seqnr              | Der Primärschlüssel                     | long     |    64 |    N     |
| kreditor_seqnr       |                                         | long     |    64 |    N     |
| bank                 | Bezeichnung Bank                        | varchar  |    60 |    J     |
| clearingnr           |                                         | varchar  |    30 |    J     |
| postkontonr          |                                         | nvarchar |   100 |    J     |
| swiftbic             |                                         | nvarchar |   100 |    J     |
| kontonr              | QR-IBAN, IBAN oder ESR-Teilnehmernummer | varchar  |    30 |    N     |
| besrkundenr          | BESR Kundennummer                       | varchar  |    30 |    N     |
| istzahlstelledefault | 1 = Default-Zahlstelle                  | smallint |    16 |    J     |
| gueltigvon           |                                         | date     |       |    N     |
| gueltigbis           |                                         | date     |       |    J     |
| insts                | Insert Timestamp (Ab Version 2.6.32)    | date     |       |    N     |
| updts                | Update Timestamp (Ab Version 2.6.32)    | date     |       |    N     |
