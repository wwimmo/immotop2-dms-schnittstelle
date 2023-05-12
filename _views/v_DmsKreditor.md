# v_DmsKreditor

In dieser View werden die Kreditoren angezeigt (Personen mit Flag Kreditor). Aktuelle Adresse mit gültig ab Datum <= Tagesdatum

## Tabellendefinition

| Name           | Kommentar                                      | Datentyp | Länge | Nullable |
| :------------- | :--------------------------------------------- | :------- | ----: | :------: |
| bez            | Die Bezeichnung                                | varchar  |   100 |    N     |
| nr             |                                                | int      |     4 |    N     |
| s_seqnr        | Der Primärschlüssel                            | key      |    64 |    N     |
| name           |                                                | varchar  |    60 |    J     |
| vorname        |                                                | varchar  |    60 |    J     |
| strasse        |                                                | varchar  |    67 |    J     |
| plz            |                                                | varchar  |    15 |    J     |
| postfach       |                                                | varchar  |    60 |    J     |
| ort            |                                                | varchar  |    60 |    J     |
| tel1           | Privat                                         | varchar  |    60 |    J     |
| tel2           | Geschäft                                       | varchar  |    60 |    J     |
| fax            |                                                | varchar  |    60 |    J     |
| homepage       |                                                | varchar  |    60 |    J     |
| email          |                                                | varchar  |   500 |    J     |
| mwstregisternr | Steuerregisternummer                           | varchar  |    30 |    N     |
| frist1         | Vorschlag: Anzahl Tage für Zahlungskondition 1 | smallint |    16 |    N     |
| insts          | Insert Timestamp (Ab Version 2.6.32)           | date     |       |    N     |
| updts          | Update Timestamp (Ab Version 2.6.32)           | date     |       |    N     |
