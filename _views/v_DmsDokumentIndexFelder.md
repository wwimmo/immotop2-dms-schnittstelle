# v_DmsDokumentIndexFelder

Indexwerte für indexieren der Dokumente im DMS System.

## Tabellendefinition

| Name                                | Kommentar                                    | Datentyp | Länge | Nullable |
| :---------------------------------- | :------------------------------------------- | :------- | ----: | :------: |
| dokument_seqnr                      | Fremdschlüssel Dokument                      | long     |    64 |    N     |
| beschreibung                        | Beschreibung                                 | varchar  | 32767 |    N     |
| dokumentart_seqnr                   | Fremdschlüssel Dokumentart                   | long     |    64 |    N     |
| dokumentartnr                       | Nummer Dokumentart                           | int      |    32 |    N     |
| dokumentartbez                      | Bezeichnung Dokumentart                      | varchar  | 32767 |    N     |
| dmsdocumentid                       | dmsdocumentid                                | long     |    64 |    N     |
| dmsdocumentguid                     | dmsdocumentguid                              | uuid     |       |    N     |
| dmsarchiv_seqnr                     | Fremdschlüssel Dmsarchiv                     | long     |    64 |    N     |
| archivuuid                          | Uuid des Archives des DMS                    | uuid     |       |    N     |
| zeitfilterstichtag                  | Zeitfilter Stichtag                          | datetime |       |    Y     |
| zeitfilterzeitraumvon               | Zeitfilter Zeitraum von                      | datetime |       |    Y     |
| zeitfilterzeitraumbis               | Zeitfilter Zeitraum bis                      | datetime |       |    Y     |
| mandant_seqnr                       | Fremdschlüssel Mandant                       | long     |    64 |    N     |
| person_seqnr                        | Fremdschlüssel Person                        | long     |    64 |    Y     |
| person                              | Info Person                                  | varchar  |       |    Y     |
| personnr                            | Nummer der Person                            | int      |    32 |    Y     |
| verhaeltniskorrespondenz_seqnr      | Fremdschlüssel Verhaeltniskorrespondenz      | long     |    64 |    Y     |
| verhaeltniskorrespondenz            | Info verhaeltniskorrespondenz                | varchar  |       |    Y     |
| liegenschaftgruppenebenkosten_seqnr | Fremdschlüssel Liegenschaftgruppenebenkosten | long     |    64 |    Y     |
| abrechnungperiode_seqnr             | Fremdschlüssel Abrechnungsperiode            | long     |    64 |    Y     |
| liegenschaft_seqnr                  | Fremdschlüssel Liegenschaft                  | long     |    64 |    Y     |
| objekt_seqnr                        | Fremdschlüssel Objekt                        | long     |    64 |    Y     |
| verhaeltnis_seqnr                   | Fremdschlüssel Verhaeltnis                   | long     |    64 |    Y     |
| mieter_seqnr                        | Fremdschlüssel Mieter                        | long     |    64 |    Y     |
| anlagetechnisch_seqnr               | Fremdschlüssel technische Anlage             | long     |    64 |    Y     |
| anlagetechnisch                     | Info technische Anlage                       | varchar  |       |    Y     |
| geraet_seqnr                        | Fremdschlüssel Geraet                        | long     |    64 |    Y     |
| geraetvondatum                      | vondatum Geraet                              | datetime |       |    Y     |
| geraet                              | Info Geraet                                  | varchar  |       |    Y     |
| geraettyp                           | Typ des Geraetes                             | varchar  |       |    Y     |
| unterhalt_seqnr                     | Fremdschlüssel Unterhalt                     | long     |    64 |    Y     |
| unterhaltnr                         | Nummer des Unterhaltes                       | int      |    32 |    Y     |
| buchhaltungperiode_seqnr            | Fremdschlüssel Buchhaltungperiode            | long     |    64 |    Y     |
| buchhaltungperiodegueltigvon        | gueltigvon Buchhaltungsperiode               | datetime |       |    Y     |
| buchhaltungperiodegueltigbis        | gueltigbis Buchhaltungsperiode               | datetime |       |    Y     |
| budgetperiode_seqnr                 | Fremdschlüssel Budgetperiode                 | long     |    64 |    Y     |
| budgetperiodevon                    | Budgetperiode von                            | datetime |       |    Y     |
| budgetperiodebis                    | Budgetperiode bis                            | datetime |       |    Y     |
| teilbuchung_seqnr                   | Fremdschlüssel Teilbuchung                   | long     |    64 |    Y     |
| teilbuchungnr                       | Nummer der Teilbuchung                       | int      |    32 |    Y     |
| buchungtext                         | Buchungtext                                  | varchar  |       |    Y     |
| beleg_seqnr                         | Fremdschlüssel Beleg                         | long     |    64 |    Y     |
| belegnummer                         | Nummer des Beleges                           | int      |    32 |    Y     |
| belegrechnungsnummer                | Belegrechnungsnummer                         | int      |    32 |    Y     |
| belegdatum                          | Belegdatum                                   | datetime |       |    Y     |
| kostenstelle_seqnr                  | Fremdschlüssel Kostenstelle                  | long     |    64 |    Y     |
| kostenstellebez                     | Bezeichnung Kostenstelle                     | varchar  |       |    Y     |
| debitorkonto_seqnr                  | Fremdschlüssel Debitorkonto                  | long     |    64 |    Y     |
| debitorkontobez                     | Bezeichnung Debitorkonto                     | varchar  |       |    Y     |
| debitorkontonr                      | Debitorkontonummer                           | int      |    32 |    Y     |
| debitorkontoart                     | Bezeichnung Debitorkontoart                  | varchar  |       |    Y     |
| kapitalkonto_seqnr                  | Fremdschlüssel Kapitalkonto                  | long     |    64 |    Y     |
| kapitalkontonr                      | Kapitalkontonr                               | int      |    32 |    Y     |
| kapitalkontoart                     | Bezeichnung Kapitalkontoart                  | varchar  |       |    Y     |
| mahnungstufe_seqnr                  | Fremdschlüssel Mahnungsstufe                 | long     |    64 |    Y     |
| mahnungstufe                        | Mahnungsstufe                                | int      |    32 |    Y     |
| mahnungtyp_seqnr                    | Fremdschlüssel Mahntyp                       | long     |    64 |    Y     |
| mahnungtyp                          | Bezeichnung Mahntyp                          | varchar  |       |    Y     |
| zahlungsliste_seqnr                 | Fremdschlüssel Zahlungsliste                 | long     |    64 |    Y     |
| zahlungsliste                       | Bezeichnung Zahlungsliste                    | varchar  |       |    Y     |
