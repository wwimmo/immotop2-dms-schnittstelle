# DmsBelegPosten

Diese Staging-Tabelle enthält die einzelnen Belegposten je Kreditorenbeleg.

- [DmsBelegPosten](#dmsbelegposten)
  - [Tabellendefinition](#tabellendefinition)
  - [MWST-Eingabeart exklusiv](#mwst-eingabeart-exklusiv)

## Tabellendefinition

| Name                        | Kommentar                                                                                                                                                                                | Daten-typ         | Null-able | Defaultwert |
| :-------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------- | --------: | :---------- |
| betragbrutto                | Der volle Betrag des BelegPostens.<br/>Er entspricht dem Bruttobetrag, falls ein MwstCode angegeben wurde, respektive dem Betrag falls keine Mwst angegeben wurde.                       | amount            |         N |             |
| betragexklmwst              | Der Betrag exklusive Mwst.<br/>Leer lassen für BelegPosten ohne MwstCode.                                                                                                                | amount            |         J |             |
| betragmwstvoll              | Der volle Steuerbetrag ohne Berücksichtigung des Vorsteueran-teils.<br/>Leer lassen für BelegPosten ohne MwstCode.<br/>betragbrutto = betragexklmwst + betragmwstvoll                    | amount            |         J |             |
| buchungtext                 | Buchungstext                                                                                                                                                                             | long descrip-tion |         N | ''          |
| dmsbeleg_seqnr              | Referenz auf den Beleg.                                                                                                                                                                  | key               |         N |             |
| faelligkeitdatum            | Nur relevant bei Buchungen auf Debitorkonten. Diese Fälligkeit bezieht sich auf die Forderung gegenüber dem Debitor.                                                                     | date              |         J |             |
| konto_seqnr                 | Referenz auf das Konto gemäss View v_DmsKonto.                                                                                                                                           | key               |         J |             |
| kostenstelle_seqnr          | Referenz auf die Kostenstelle gemäss View v_DmsKostenstelle.                                                                                                                             | key               |         J |             |
| mahnungtyp_seqnr            | Referenz auf den MahnungTyp gemäss View v_DmsMahnungTyp.<br/>Angabe erforderlich bei Verwendung eines Debitorkontos.                                                                     | key               |         J |             |
| menge                       | Beim Buchen auf ein Kostenkonto, das eine Mengenangabe hinterlegt hat, kann die Menge mitgegeben werden.                                                                                 | decimal 12.3      |         J |             |
| mwstabrechnungziffer_seqnr  | Referenz auf die MwstAbrechnungZiffer gemäss View v_DmsMwstAbrechnungZiffer.<br/>Diese Angabe wird nur in wenigen Fällen gebraucht.                                                      | key               |         J |             |
| mwstcode_seqnr              | Referenz auf den MwstCode gemäss View v_DmsMwstCode.                                                                                                                                     | key               |         J |             |
| mwstsatz                    | Der Mwst-Satz, zum Beispiel: 7.70.                                                                                                                                                       | decimal (9.2)     |         J |             |
| mwstsatzdatum               | Datum um den Mwst-Satz zu ermitteln                                                                                                                                                      | date              |         J |
| nkabrechnungperiodestichtag | Nebenkosten-Abrechnungsperiode-Stichtag<br/>Falls Nebenkosten-Abrechnungsperioden-Nummer nicht ausgefüllt ist, wird die Nebenkosten-Abrechnungsperiode mit diesem Stichtag bestimmt.     | date              |         J |             |
| nr                          | Die Nummer dient zur Sortierung der Belegposten je Beleg.                                                                                                                                | int               |         J |             |
| preisproeinheit             | Preis pro Einheit. Die Einheit ist beim Konto in der Buchhaltung hinterlegt (v_DmsKonto).                                                                                                | amount            |         J |             |
| vorsteueranteil             | Der Vorsteueranteil wird bei teiloptierten Liegenschaften verwendet. Ist der Wert NULL, so berechnet ImmoTop2 den Vorsteueranteil selbst. Ist er abgefüllt, so wird der Wert übernommen. | decimal (9,3)     |         J |             |

## MWST-Eingabeart exklusiv

Wenn die Felder wie oben beschrieben abgefüllt werden, handelt es sich um einen Belegposten mit der WMST-Eingabeart "inklusiv". Für den Fall, dass man einen Belegposten mit der MWST-Eingabeart "exklusiv" erfassen will, muss man die Felder wie folgt abfüllen:

- betragbrutto: Betrag exklusiv MWST
- betragexklmwst: Betrag exklusiv MWST
- betragmwstvoll: Der volle Steuerbetrag

Der Betrag inklusiv MWST wird dann vom System berechnet.
