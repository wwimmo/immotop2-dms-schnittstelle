# v_DmsImportStatus

In dieser View werden die Status beim Importieren von Dokumenten angezeigt. 

## Tabellendefinition

| Name    | Kommentar           | Datentyp | Länge | Nullable |
| :------ | :------------------ | :------- | ----: | :------: |
| s_seqnr | Der Primärschlüssel | key      |    64 |    N     |
| nr      | Nummer des Eintrags | int      |    32 |    N     |
| bez     | Die Bezeichnung     | varchar  |   100 |    N     |


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
