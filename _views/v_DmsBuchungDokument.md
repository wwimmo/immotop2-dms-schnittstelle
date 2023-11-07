# v_DmsBuchungDokument

In dieser View werden die Buchungsinformationen zu einem Dokument angezeigt.

## Tabellendefinition

| Name                    | Kommentar                             | Datentyp | Länge | Nullable |
| :---------------------- | :------------------------------------ | :------- | ----: | :------: |
| s_seqnr                 | Der Primärschlüssel                   | long     |    64 |    N     |
| strichcode              | Strichcode oder QR-Code               | nvarchar |   100 |    J     |
| sollkonto_seqnr         | Primärschlüssel des Soll Konto        | long     |    64 |    N     |
| sollkontonr             | Nummer des Sollkontos                 | int      |    32 |    N     |
| habenkonto_seqnr        | Primärschlüssel des Haben Konto       | long     |    64 |    N     |
| habenkontonr            | Nummer des Haben Konto                | int      |    32 |    N     |
| habenkostenstelle_seqnr | Primärschlüssel der Habenkostenstelle | long     |    64 |    J     |
| habenkostenstelle       | Die Haben Kostenstelle                | nvarchar |   100 |    J     |
| buchungsdatum           | Datum der Buchung                     | date     |       |    J     |
| betrag                  | Der Betrag der Buchung.               | decimal  |  12,2 |    J     |
| mandant_seqnr           | Primärschlüssel des Mandanten.        | long     |    64 |    N     |
| mandantnr               | Nummer des Mandanten                  | int      |    32 |    N     |
