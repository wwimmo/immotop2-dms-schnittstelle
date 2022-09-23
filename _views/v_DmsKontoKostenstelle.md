# v_DmsKontoKostenstelle

Diese View zeigt, welche Kostenstellen bei welchem Konto zulässig sind. Die Gültigkeit der Kostenstellen ist gegeben durch das Gültig-von-Datum und Gültig-bis-Datum.

## Tabellendefinition

| Name               | Kommentar                                   | Datentyp | Länge | Nullable |
| :----------------- | :------------------------------------------ | :------- | ----: | :------: |
| konto_seqnr        | Das Konto.                                  | bigint   |    64 |    N     |
| kostenstelle_seqnr | Eine der passenden Kostenstellen zum Konto. | bigint   |    64 |    N     |
| gueltigvon         | Gültig-von-Datum der Kostenstelle.          | date     |       |    N     |
| gueltigbis         | Gültig-bis-Datum der Kostenstelle.          | date     |       |    J     |
