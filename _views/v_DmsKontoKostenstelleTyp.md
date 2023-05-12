# v_DmsKontoKostenstelleTyp

Diese View zeigt, welche Kostentypen bei welchem Konto zulässig sind. 

## Tabellendefinition

| Name                    | Kommentar                             | Datentyp | Länge | Nullable |
| :---------------------- | :------------------------------------ | :------- | ----: | :------: |
| konto_seqnr             | Primärschlüssel des Kontos            | bigint   |    64 |    N     |
| kostenstelletyp_seqnr   | Primärschlüssel des Kostenstellentyps | bigint   |    64 |    N     |
| kostenstelletyp_nr      | Nummer des Kostenstellentyps          | int      |    32 |    N     |
| kostenstelletyp_kennung | Kennung des Kostenstellentyps         | nvarchar |    10 |    N     |
| kostenstelletyp_bez     | Bezeichung des Kostenstellentyps      | nvarchar |   100 |    N     |
| insts                   | Insert Timestamp (Ab Version 2.6.32)  | date     |       |    N     |
| updts                   | Update Timestamp (Ab Version 2.6.32)  | date     |       |    N     |
