# v_DmsUnterhalt

View über alle Unterhalte.

## Tabellendefinition

| Name                | Kommentar                           | Datentyp | Länge | Nullable |
| :------------------ | :---------------------------------- | :------- | ----: | :------: |
| s_seqnr             | Der Primärschlüssel                 | long     |    64 |    N     |
| mandant_seqnr       | Primärschlüssel des Mandanten       | long     |    64 |    N     |
| liegenschaft_seqnr  | Primärschüssel der Liegenschaft     | long     |    64 |    J     |
| objekt_seqnr        | Primärschlüssel des Objektes        | long     |    64 |    J     |
| person_seqnr        | Primärschlüssel der Person          | long     |    64 |    J     |
| geraet_seqnr        | Primärschlüssel des Gerätes         | long     |    64 |    J     |
| geraettyp_seqnr     | Primärschlüssel des Gerätetyps      | long     |    64 |    J     |
| bkphelement_seqnr   | Primärschlüssel des BKP-H-Elementes | long     |    64 |    J     |
| nr                  | Nummer                              | int      |    32 |    N     |
| bemerkung           | Bemerkung zum Unterhalt             | nvarchar | 32767 |    N     |
| betreff             | Betreff zum Unterhalt               | nvarchar | 32767 |    N     |
| auftragnummerextern | Externe Auftragsnummer              | nvarchar |   100 |    N     |
| kosten              | Kosten                              | decimal  |  12,2 |    J     |
| status              | Status des Unterhalts               | nvarchar |   100 |    N     |
| statusnr            | Statusnummer                        | int      |    32 |    N     |
| statusgueltigab     | Gültigab Datum des Status           | date     |       |    J     |
| insts               | Insert Timestamp                    | date     |       |    N     |
| updts               | Update Timestamp                    | date     |       |    N     |
