# v_DmsLiegenschaft

View über alle Liegnschaften.

## Tabellendefinition

| Name               | Kommentar                                   | Datentyp | Länge | Nullable |
| :----------------- | :------------------------------------------ | :------- | ----: | :------: |
| s_seqnr            | Der Primärschlüssel                         | long     |    64 |    N     |
| nr                 | Nummer der Liegenschaft                     | int      |    32 |    N     |
| bez                | Bezeichnung                                 | nvarchar |       |    N     |
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
| buchhalter_seqnr   | Primärschlüssel Buchhalter (Verwalter)      | long     |    64 |    J     |
| buchhalter         | Vorname + ' ' + Nachname                    | nvarchar |       |    N     |
| buchhalter2_seqnr  | Primärschlüssel Buchhalter 2 (Verwalter 2)  | long     |    64 |    J     |
| buchhalter2        | Vorname + ' ' + Nachname                    | nvarchar |       |    N     |
| insts              | Insert Timestamp (Ab Version 2.6.32)        | date     |       |    N     |
| updts              | Update Timestamp (Ab Version 2.6.32)        | date     |       |    N     |

- Buchhalter wurde mit der Version 2.6.25 hinzugefügt.
- Bezeichnung wurde mit der Version 2.6.35 hinzugefügt.
