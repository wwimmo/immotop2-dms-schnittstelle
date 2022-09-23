# v_DmsImportFehlerCode

In dieser View werden die Fehlercodes beim importieren der Dokumente angezeigt. 

## Tabellendefinition

| Name    | Kommentar           | Datentyp | Länge | Nullable |
| :------ | :------------------ | :------- | ----: | :------: |
| s_seqnr | Der Primärschlüssel | key      |    64 |    N     |
| nr      | Nummer des Eintrags | int      |    32 |    N     |
| bez     | Die Bezeichnung     | varchar  |   100 |    N     |

## Fehlercodes

| Nummer | Fehlercode                                                                                                                             |
| :----- | :------------------------------------------------------------------------------------------------------------------------------------- |
| -1     | Der Beleg konnte nicht importiert werden.                                                                                              |
| -10    | Der Lizenzpunkt «DMS Schnittstelle» ist nicht aktiv.                                                                                   |
| -300   | Tabelle DmsImport: Die dmsdocumentid fehlt.                                                                                            |
| -301   | Tabelle DmsImport: Das Dokument befindet sich unter der dmsdocumentid nicht im Dms-Archiv.                                             |
| -302   | Tabelle DmsImport: Der Datensatz wird bei mehreren DmsBeleg verwendet.                                                                 |
| -303   | Tabelle DmsImport: Zum Datensatz in DmsImport gibt es in der Tabelle DmsBeleg keinen passenden Eintrag – die Daten sind unvollständig. |
| -304   | Tabelle DmsImport: Die dmsarchiveguid fehlt.                                                                                           |
| -305   | Tabelle DmsImport: Die dmsarchiveguid ist nicht vorhanden.                                                                             |
| -307   | Tabelle DmsImport: Unstimmigkeit im Dms beim DmsImport.                                                                                |
| -310   | Tabelle DmsImport: DmsDateiname ist leer.                                                                                              |
| -500   | Tabelle DmsBeleg: Der Kreditorenbeleg ist bereits vorhanden.                                                                           |
| -502   | Tabelle DmsBeleg: Die angegebene belegartnr ist nicht zulässig.                                                                        |
| -503   | Tabelle DmsBeleg: Die belegnummer ist zu lang.                                                                                         |
| -504   | Tabelle DmsBeleg: Es sind keine Belegposten vorhanden.                                                                                 |
| -505   | Tabelle DmsBeleg: Das Belegdatum ist nicht korrekt.                                                                                    |
| -507   | Tabelle DmsBeleg: Beim Validieren des Beleges sind Unstimmigkeiten aufgetreten.                                                        |
| -508   | Tabelle DmsBeleg: Der Beleg konnte nicht gespeichert werden.                                                                           |
| -509   | Tabelle DmsBeleg: Wenn eine ESR-Zahlstelle verwendet wird, muss die esrreferenznummer angegeben werden.                                |
| -521   | Tabelle DmsBeleg: Kein Mandant angegeben.                                                                                              |
| -522   | Tabelle DmsBeleg: Der Mandant existiert nicht.                                                                                         |
| -528   | Tabelle DmsBeleg: Die angegebene zahlstellemandant_seqnr existiert nicht.                                                              |
| -550   | Tabelle DmsBeleg: Es wurde keine kreditor_seqnr angegeben.                                                                             |
| -551   | Tabelle DmsBeleg: Es gibt keinen Kreditor mit der angegebenen kreditor_seqnr.                                                          |
| -552   | Tabelle DmsBeleg: Beim Kreditor ist weder die kreditor_seqnr noch Name mit Plz angegeben.                                              |
| -553   | Tabelle DmsBeleg: Die Plz stimmt nicht mit den Stammdaten überein.                                                                     |
| -555   | Tabelle DmsBeleg: Der Kreditor hat keine Zahlstellen.                                                                                  |
| -556   | Tabelle DmsBeleg: Der Kreditor konnte nicht gesetzt werden.                                                                            |
| -580   | Tabelle DmsBeleg: Keine Angaben zur Kreditorenzahlstelle vorhanden.                                                                    |
| -581   | Tabelle DmsBeleg: Die angegebene zahlstellekreditor_seqnr existiert nicht.                                                             |
| -582   | Tabelle DmsBeleg: Die Zahlstelle mit der zahlstellekreditor_seqnr gehört nicht zum gewünschten Kreditor.                               |
| -583   | Tabelle DmsBeleg: Die Kontonummer bei der Zahlstelle stimmt nicht überein.                                                             |
| -584   | Tabelle DmsBeleg: Die Kontonummer ist keine gültige Iban.                                                                              |
| -585   | Tabelle DmsBeleg: Die Kontonummer darf nur bei Bank- oder Post-Konto leer gelassen werden.                                             |
| -587   | Tabelle DmsBeleg: Die Zahlstelle ist nicht gültig.                                                                                     |
| -588   | Tabelle DmsBeleg: Unstimmigkeiten bei der Referenzzeile des Einzahlungsscheines.                                                       |
| -590   | Tabelle DmsBeleg: Die Zahlungskondition ist nicht gültig.                                                                              |
| -800   | Tabelle DmsBelegPosten: Die Abrechnungsperiode hat den Status abgerechnet und kann nicht verwendet werden.                             |
| -801   | Tabelle DmsBelegPosten: Die Abrechnungsperiode ist per Stichtag nicht vorhanden.                                                       |
| -802   | Tabelle DmsBelegPosten: Das Konto ist ungültig.                                                                                        |
| -803   | Tabelle DmsBelegPosten: Die Kostenstelle ist ungültig.                                                                                 |
| -806   | Tabelle DmsBelegPosten: Der Rechnungsbetrag stimmt nicht mit der Summe der Beträge von den Belegposten überein.                        |
| -807   | Tabelle DmsBelegPosten: Das Konto verlangt keine Kostenstelle.                                                                         |
| -808   | Tabelle DmsBelegPosten: Die Beträge sind nicht korrekt; es ist kein Mwst-Satz vorhanden.                                               |
| -809   | Tabelle DmsBelegPosten: Der Mwst-Satz fehlt.                                                                                           |
| -810   | Tabelle DmsBelegPosten: Die Kostenstelle konnte nicht gesetzt werden.                                                                  |
| -811   | Tabelle DmsBelegPosten: Der Buchungstext konnte nicht gesetzt werden.                                                                  |
| -812   | Tabelle DmsBelegPosten: Der Betrag konnte nicht gesetzt werden.                                                                        |
| -813   | Tabelle DmsBelegPosten: Zum Konto gibt es keine Kostenstellen.                                                                         |
| -814   | Tabelle DmsBelegPosten: Zum Konto gibt es mehrere Kostenstellen.                                                                       |
| -815   | Tabelle DmsBelegPosten: Die Mengenangaben konnten nicht gesetzt werden.                                                                |
| -816   | Tabelle DmsBelegPosten: Es gibt Unstimmigkeiten bei den Mwst-Angaben.                                                                  |
| -817   | Tabelle DmsBelegPosten: Der Mahntyp ist ungültig.                                                                                      |
| -818   | Tabelle DmsBelegPosten: Es gibt Unstimmigkeiten beim Mwst-Satz.                                                                        |
