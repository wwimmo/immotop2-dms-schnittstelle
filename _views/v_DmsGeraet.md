# v_DmsGeraet

View über alle Geraete.

## Tabellendefinition

| Name                  | Kommentar                              | Datentyp | Länge | Nullable |
| :-------------------- | :------------------------------------- | :------- | ----: | :------: |
| s_seqnr               | Der Primärschlüssel                    | long     |    64 |    N     |
| mandant_seqnr         | Primärschlüssel des Mandanten          | long     |    64 |    N     |
| liegenschaft_seqnr    | Primärschüssel der Liegenschaft        | long     |    64 |    J     |
| objekt_seqnr          | Primärschlüssel des Objektes           | long     |    64 |    J     |
| geraettyp_seqnr       | Primärschlüssel des Gerätetyps         | long     |    64 |    J     |
| bkphelement_seqnr     | Primärschlüssel des BKP-H-Elementes    | long     |    64 |    J     |
| anlagetechnisch_seqnr | Primärschlüssel der technischen Anlage | long     |    64 |    J     |
| bemerkung             | Bemerkung zum Geraet                   | nvarchar | 32767 |    N     |
| marke                 | Marke des Geraetes                     | nvarchar |   100 |    N     |
| modell                | Modell des Geraetes                    | nvarchar |   100 |    N     |
| hersteller            | Hersteller des Geraetes                | nvarchar |   100 |    N     |
| gueltigvon            | Gültig-von-Datum des Geraetes          | date     |       |    N     |
| gueltigbis            | Gültig-bis-Datum des Geraetes          | date     |       |    J     |
| insts                 | Insert Timestamp                       | date     |       |    N     |
| updts                 | Update Timestamp                       | date     |       |    N     |
