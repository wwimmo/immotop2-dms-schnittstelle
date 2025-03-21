# DmsBelegPostenGeraet

In dieser Tabelle kann ein Geraet zu einem BelegPosten erfasst werden.

Ein Gerät wird einem Mandanten, einer Liegenschaft oder einem Objekt zugeordnet.

- Wenn das Gerät direkt dem Mandanten zugeordnet wird, muss nur der Mandant angegeben werden.
- Wenn das Gerät einer Liegenschaft zugeordnet wird, muss der Mandant und die Liegenschaft angegeben werden.
- Wenn das Gerät einem Objekt zugeordnet wird, muss der Mandant, die Liegenschaft und das Objekt angegeben werden.

_Verfügbar ab Version 2.7.23_

## Tabellendefinition

| Name                      | Kommentar                                                                                    | Daten-typ        | Null-able | Defaultwert |
| ------------------------- | -------------------------------------------------------------------------------------------- | ---------------- | --------- | ----------- |
| anlagetechnisch_seqnr     | Technische Anlage, zu welcher das Gerät gehört, falls es zu einer technischen Anlage gehört. | key              | Y         |             |
| anschaffungskosten        | Anschaffungskosten des Geräts.                                                               | amount           | Y         | 0.00        |
| bemerkung                 | Bemerkung zu Gerät.                                                                          | long description | N         | ''          |
| bkphelement_seqnr         | FK zu bkphelement                                                                            | key              | Y         |             |
| dmsbelegposten_seqnr      | FK zu dmsbelegposten                                                                         | key              | N         |             |
| geraettyp_seqnr           | FK zu geraettyp                                                                              | key              | Y         |             |
| gueltigbis                | Gerät ist bis zu diesem Datum gültig.                                                        | date             | Y         |             |
| gueltigvon                | Gerät ist ab diesem Datum gültig.                                                            | date             | N         | getdate()   |
| hersteller                | Herstelle des Geräts. Z. B. V-Zug.                                                           | text             | Y         | ''          |
| katalogpreis              | Katalogpreis des Geräts.                                                                     | amount           | Y         | 0.00        |
| kuendigungsbedingungen    | Kündigungsbedingungen für den Service.                                                       | text             | N         | ''          |
| letzteamtlichekontrolle   | Letzte amtliche Kontrolle des Geräts.                                                        | date             | Y         |             |
| letzterevision            | Letzte Revision des Geräts.                                                                  | date             | Y         |             |
| liegenschaft_seqnr        | FK zur Liegenschaft                                                                          | key              | Y         |             |
| mand_seqnr                | FK zum Mandanten                                                                             | key              | N         |             |
| marke                     | Marke des Geräts. Z. B. V-Zug.                                                               | text             | N         |             |
| modell                    | Modell des Geräts. Z. B. GS-Beta 2000-S.                                                     | text             | N         |             |
| naechsteamtlichekontrolle | Nächste amtliche Kontrolle des Geräts.                                                       | date             | Y         |             |
| naechsterevision          | Nächste Revision des Geräts.                                                                 | date             | Y         |             |
| objekt_seqnr              | FK zum Objekt                                                                                | key              | Y         |             |
| personablesefirma_seqnr   | Firma, welche die Zählerstände prüft.                                                        | key              | Y         |             |
| personlieferant_seqnr     | Lieferant des Geräts.                                                                        | key              | Y         |             |
| personwartungfirma_seqnr  | Wartungsfirma des Geräts.                                                                    | key              | Y         |             |
| produktnummerncode        | Produktnummer des Produkts.                                                                  | text             | N         | ''          |
| seriennummer              | Seriennummer des Geräts. Z. B. 115.558.235.X.                                                | text             | N         | ''          |
| serviceabobis             | Service-Abo für das Gerät bis.                                                               | date             | Y         |             |
| serviceabovon             | Service-Abo für das Gerät von.                                                               | date             | Y         |             |
| servicebedingungen        | Bedingungen für den Geräte-Service.                                                          | text             | N         | ''          |
