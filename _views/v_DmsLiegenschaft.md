# v_DmsLiegenschaft

View über alle Liegnschaften.

## Tabellendefinition

| Name               | Kommentar                                   | Datentyp | Länge | Nullable |
| :----------------- | :------------------------------------------ | :------- | ----: | :------: |
| s_seqnr            | Der Primärschlüssel                         | long     |    64 |    N     |
| nr                 | Nummer der Liegenschaft                     | int      |    32 |    N     |
| mandant_seqnr      | Primärschlüssel des Mandanten               | long     |    64 |    N     |
| mandant_nr         | Nummer des Mandanten                        | int      |    32 |    N     |
| lieggruppenk_seqnr | Primärschlüssel Liegenschaftengruppe NK     | long     |    64 |    J     |
| grundbuchanmerkung | Die Anmerkung zum Grundbucheintrag          | nvarchar |  2048 |    N     |
| strasse            | Strasse                                     | nvarchar |   100 |    N     |
| plzort             | Postleitzahl + ' '  + Ort                   | nvarchar |       |    N     |
| mitarbeiter_seqnr  | Primärschlüssel Mitarbeiter (Verwalter)     | long     |    64 |    J     |
| mitarbeiter        | Vorname + ' ' + Nachname                    | nvarchar |       |    N     |
| mitarbeiter2_seqnr | Primärschlüssel Mitarbeiter 2 (Verwalter 2) | long     |    64 |    J     |
| mitarbeiter2       | Vorname + ' ' + Nachname                    | nvarchar |       |    N     |
