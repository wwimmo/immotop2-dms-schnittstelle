# v_DmsAbrechnungPeriode

In dieser View befinden sich die Abrechnungsperioden. Ihre Gültigkeit ist gegeben durch das Gültig-von-Datum und Gültig-bis-Datum. 

Wenn eine Kostenstelle angegeben wurde, muss gewährleistet sein, dass es entweder keine zugehörige Abrechnungsperiode gibt oder dass sie den Abrechnungsstatus ‘nicht aufgerechnet’ hat.

Im Detail heisst das: Von der Kostenstelle gelangen wir über das Feld liegenschaftgruppenebenkosten_seqnr zur Liegenschaftgruppe. Das Feld kann auch leer sein, in diesem Fall ist ein weiteres Prüfen nicht nötig. Die zugehörige Abrechnungsperiode  wird mittels der Liegenschaftgruppe und dem Buchungsdatum gesucht. Falls es keine gibt, ist ein weiteres Prüfen nicht nötig. Wenn es eine gibt, muss sie 1 als abrechnungstatusnr haben. Vorsicht: Nur bei Mandanten mit Mandanttypcode ‘S’ gilt das Buchungsdatum als Stichdatum für die Abrechnungsperiode. Bei den anderen Mandanten wird der nkabrechnungperiodestichtag des DmsBelegPostens genommen, falls angegeben, andernfalls kommt das BelegDatum gemäss DmsBeleg zum Zug.

## Tabellendefinition

| Name                                | Kommentar                                                                                          | Datentyp | Länge | Nullable |
| :---------------------------------- | :------------------------------------------------------------------------------------------------- | :------- | ----: | :------: |
| abrechnungperiode_seqnr             | Der Primärschlüssel                                                                                | bigint   |    64 |    N     |
| mandant_seqnr                       | Der Mandant.                                                                                       | bigint   |    64 |    N     |
| mandnr                              | Die Mandantennummer                                                                                | Int      |    31 |    N     |
| liegenschaftgruppenebenkosten_seqnr | Die Liegenschaftengruppe. Liegenschaftengruppen können unterschiedliche Abrechnungsperioden haben. | bigint   |    64 |    N     |
| gueltigvon                          | Gültig-von-Datum der Abrechnungsperiode                                                            | date     |       |    N     |
| gueltigbis                          | Gültig-bis-Datum der Abrechnungsperiode                                                            | date     |       |    J     |
| abrechnungstatusnr                  | 1 = nicht aufgerechnet, 2 = aufgerechnet, 3 = abgeschlossen                                        | int      |    32 |    N     |
| insts                               | Insert Timestamp (Ab Version 2.6.32)                                                               | date     |       |    N     |
| updts                               | Update Timestamp (Ab Version 2.6.32)                                                               | date     |       |    N     |
