# v_DmsBelegCode

View der BelegCodes.

## Tabellendefinition

| Name         | Kommentar                            | Datentyp | Länge | Nullable |
| :----------- | :----------------------------------- | :------- | ----: | :------: |
| s_seqnr      | Der Primärschlüssel                  | long     |    64 |    N     |
| kuerzel      | Kuerzel                              | varchar  |   100 |    N     |
| beschreibung | Beschreibung                         | varchar  | 32767 |    Y     |
| insts        | Insert Timestamp (Ab Version 2.6.32) | date     |       |    N     |
| updts        | Update Timestamp (Ab Version 2.6.32) | date     |       |    N     |
