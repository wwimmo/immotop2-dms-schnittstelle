# v_DmsImportStatus

In dieser View werden die Status beim Importieren von Dokumenten angezeigt. 

## Tabellendefinition

| Name    | Kommentar   |
| ------- | ----------- |
| s_seqnr | Primary Key |
| bez     | Bezeichnung |
| nr      | Nummer      |

## verwendete Status

| Id  | Status                 |
| --- | ---------------------- |
| 0   | bereit zum Import      |
| 1   | in Arbeit              |
| 2   | erfolgreich importiert |
| -1  | fehlerhafter Import    |
| -2  | fehlerhafte Lieferung  |
| -3  | blockiert im ImmoTop2  |
| -4  | löschen                |
