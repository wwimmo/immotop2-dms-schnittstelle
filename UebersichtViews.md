# ImmoTop2 Datenbank-Views

Die nachfolgenden Views dienen der Workflow Engine des DMS dazu, die zulässigen Datenkombinationen zu ermitteln. Fragen, die beantwortet werden, sind: 

- Existiert der Kreditor bereits?
- Wie ist der Kontenrahmen des Mandanten?
- Welche Kostenstellen passen zum gewählten Konto?
- Soll mit Mwst gebucht werden oder nicht?
- Etc.

| View                                                                               | Details                                                     |
| :--------------------------------------------------------------------------------- | :---------------------------------------------------------- |
| [v_DmsImportFehlerCode](./_views/v_DmsImportFehlerCode.md)                         | View mit den Fehlercodes für das Importieren von Dokumenten |
| [v_DmsImportStatus](./_views/v_DmsImportStatus.md)                                 | Status der Importierten von Dokumente                       |
| [v_DmsMandant](./_views/v_DmsMandant.md)                                           | Information zu den Mandanten                                |
| [v_DmsMandantZahlstelle](./_views/v_DmsMandantZahlstelle.md)                       | Infromation zur Zahlstelle des Mandanten                    |
| [v_DmsKreditor](./_views/v_DmsKreditor.md)                                         | Informationen zu den Kreditoren                             |
| [v_DmsKreditorZahlstelle](./_views/v_DmsKreditorZahlstelle.md)                     | Zahlstellen der Kreditoren                                  |
| [v_DmsKonto](./_views/v_DmsKonto.md)                                               | Kontenplan                                                  |
| [v_DmsExportKonto](./_views/v_DmsExportKonto.md)                                   | Details zum Exportkonto.                                    |
| [v_DmsKontoKostenstelleTyp](./_views/v_DmsKontoKostenstelleTyp.md)                 | Kostenstellentyp pro Konto                                  |
| [v_DmsKontoKostenstelle](_views/v_DmsKontoKostenstelle.md)                         | Zulässige Kostenstelle pro Konto                            |
| [v_DmsKostenstelle](_views/v_DmsKostenstelle.md)                                   | Informationen zu den Kostenstellen                          |
| [v_DmsExportKostenstelle](_views/v_DmsExportKostenstelle.md)                       | Details zu Exportkostenstelle                               |
| [v_DmsMwstAbrechnungZiffer](_views/v_DmsMwstAbrechnungZiffer.md)                   | Mwst Abrechnungsziffern                                     |
| [v_DmsVorsteuerAnteil](_views/v_DmsVorsteuerAnteil.md)                             | Vorsteueranteile                                            |
| [v_DmsKostenGruppeKostenKonto](_views/v_DmsKostenGruppeKostenKonto.md)             | Vorsteueranteil zum Kostenkonto                             |
| [v_DmsMahnungTyp](_views/v_DmsMahnungTyp.md)                                       | Auswahl der möglichen Mahntypen                             |
| [v_DmsMwstCode](_views/v_DmsMwstCode.md)                                           | Mwst Codes                                                  |
| [v_MwstSatz](_views/v_DmsMwstSatz.md)                                              | Mwst Satz                                                   |
| [v_DmsAbrechnungPeriode](_views/v_DmsAbrechnungPeriode.md)                         | Abrechnungsperioden                                         |
| [v_DmsBelegCode](_views/v_DmsBelegCode.md)                                         | Belegcode                                                   |
| [v_DmsObjekt](_views/v_DmsObjekt.md)                                               | Informationen zu den Objekten                               |
| [v_DmsMieter](_views/v_DmsMieter.md)                                               | Informationen zu den Mietern                                |
| [v_DmsVerhaeltnis](_views/v_DmsVerhaeltnis.md)                                     | Informationen zu den Verhältnissen                          |
| [v_DmsCode](_views/v_DmsCode.md)                                                   | Codes                                                       |
| [v_DmsLiegenschaft](_views/v_DmsLiegenschaft.md)                                   | Informationen zu den Liegenschaften                         |
| [v_DmsLiegenschaftGruppeNebenkosten](_views/v_DmsLiegenschaftGruppeNebenkosten.md) | Informationen zu den Liegenschaftengruppe Nebenkosten       |
| [v_DmsBuchungDokument](_views/v_DmsBuchungDokument.md)                             | Buchungen zu deinem Dokument                                |
| [v_DmsMitarbeiter](_views/v_DmsMitarbeiter.md)                                     | Informationen zu den Mitarbeitern                           |
| [v_DmsZahlungposten](_views/v_DmsZahlungposten.md)                                 | Informationen zu den Zahlungen                              |
| [v_DmsBelegzahlungAngaben](_views/v_DmsBelegzahlungAngaben.md)                     | Angaben zu den Belegzahlungen                               |
| [v_DmsDokumentIndexFelder](_views/v_DmsDokumentIndexFelder.md)                     | Indexfelder für DMS                                         |
| [v_DmsGeraet](_views/v_DmsGeraet.md)                                               | Informationen zu den Geräten                                |
| [v_DmsGeraetTyp](_views/v_DmsGeraetTyp.md)                                         | Informationen zu den Gerätetypen                            |
| [v_DmsAnlageTechnisch](_views/v_DmsAnlageTechnisch.md)                             | Informationen zu den technischen Anlagen                    |
| [v_DmsBkphElement](_views/v_DmsBkphElement.md)                                     | Informationen zu den BKP-H-Elementen                        |
| [v_DmsBkphElementGruppe](_views/v_DmsBkphElementGruppe.md)                         | Informationen zu den BKP-H-Elementen Gruppen                |
| [v_DmsUnterhalt](_views/v_DmsUnterhalt.md)                                         | Informationen zu den Unterhalten                            |
