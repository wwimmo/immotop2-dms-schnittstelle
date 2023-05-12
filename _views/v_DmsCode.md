# v_DmsCode

Im Gegensatz zu ImmoTop kann in ImmoTop2 ein Fachobjekt mehrere Codes beinhalten. Diese View dient dazu, die Codes eines Fachobjekts zu lesen.

In einem ersten Schritt ist das für Liegenschaft umgesetzt.

## Tabellendefinition

| Name               | Kommentar                            | Datentyp | Länge | Nullable |
| :----------------- | :----------------------------------- | :------- | ----: | :------: |
| s_seqnr            | Der Primärschlüssel                  | long     |    64 |    N     |
| kuerzel            | Kürzel des Codes                     | nvarchar |   100 |    N     |
| beschreibung       | Beschreibung des Codes               | nvarchar | 32767 |    N     |
| liegenschaft_seqnr | Primärschlüssel der Liegenschaft     | long     |    64 |    J     |
| insts              | Insert Timestamp (Ab Version 2.6.32) | date     |       |    N     |
| updts              | Update Timestamp (Ab Version 2.6.32) | date     |       |    N     |
