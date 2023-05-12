# v_DmsMandantZahlstelle

Hier erscheinen alle Zahlstellen zum Mandanten. Der passende Eintrag kann via mandant_seqnr oder person_seqnr gesucht werden, wobei die Person zum Mandanten den Eigentümer repräsentiert. Die Gültigkeit der Zahlstellen ist gegeben durch das Gültig-von-Datum und Gültig-bis-Datum.

## Tabellendefinition

| Name             | Kommentar                                      | Datentyp | Länge | Nullable |
| :--------------- | :--------------------------------------------- | :------- | ----: | :------: |
| bez              | Die Bezeichnung                                | varchar  |   100 |    N     |
| mandant_seqnr    | Der Mandant.                                   | bigint   |    64 |    N     |
| Person_seqnr     | Die Person des Mandanten                       | bigint   |    64 |    N     |
| zahlstelle_seqnr | Die Zahlstelle zum Mandanten.                  | bigint   |    64 |    N     |
| bankbez          | Bezeichnung der Bank.                          | varchar  |   100 |    N     |
| bankclearingnr   | Clearing-Nummer der Bank.                      | int      |    32 |    J     |
| bankort          | *                                              | varchar  |   100 |    N     |
| bankplz          | *                                              | varchar  |   100 |    N     |
| gueltigvon       | Gültig-von-Datum der Zahlstelle                | date     |       |    N     |
| gueltigbis       | Gültig-bis-Datum der Zahlstelle                | date     |       |    J     |
| kontonr          | Kontonummer der Zahlstelle, respektive QR-Iban | varchar  |    40 |    N     |
| zahlstelletypbez | *                                              | varchar  |   100 |    N     |
| zahlstelletypnr  | *                                              | int      |    32 |    N     |
| insts            | Insert Timestamp (Ab Version 2.6.32)           | date     |       |    N     |
| updts            | Update Timestamp (Ab Version 2.6.32)           | date     |       |    N     |
