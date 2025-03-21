# v_DmsUnterhaltStatus

In dieser View werden die Status eines Unterhalt angezeigt.

_Verfügbar ab Version 2.7.23_

## Tabellendefinition

| Name    | Kommentar           | Datentyp | Länge | Nullable |
| :------ | :------------------ | :------- | ----: | :------: |
| s_seqnr | Der Primärschlüssel | key      |    64 |    N     |
| nr      | Nummer des Eintrags | int      |    32 |    N     |
| kuerzel | Kuerzel des Status  | varchar  |   100 |    N     |
| bez     | Die Bezeichnung     | varchar  |   100 |    N     |
