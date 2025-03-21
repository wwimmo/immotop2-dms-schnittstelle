# DmsBelegPostenUnterhalt

In dieser Tabelle kann ein Unterhalt zu einem BelegPosten erfasst werden.

Ein Unterhalt wird einem Mandanten, einer Liegenschaft oder einem Objekt zugeordnet.

- Wenn der Unterhalt direkt dem Mandanten zugeordnet wird, muss nur der Mandant angegeben werden.
- Wenn der Unterhalt einer Liegenschaft zugeordnet wird, muss der Mandant und die Liegenschaft angegeben werden.
- Wenn der Unterhalt einem Objekt zugeordnet wird, muss der Mandant, die Liegenschaft und das Objekt angegeben werden.

_Verfügbar ab Version 2.7.23_

## Tabellendefinition

| Name                  | Kommentar                                 | Daten-typ        | Null-able | Defaultwert |
| --------------------- | ----------------------------------------- | ---------------- | --------- | ----------- |
| abuhrzeit             | Feld für die Uhrzeit ab.                  | text             | Y         |             |
| arbeitenab            | Beginndatum der Arbeiten.                 | date             | Y         |             |
| arbeitenbis           | Arbeiten erledigt bis.                    | date             | Y         |             |
| auftragnummerextern   | Externe Auftragsnummer für den Unterhalt. | text             | Y         | ''          |
| bemerkung             | Bemerkung zum Unterhalt.                  | long description | N         | ''          |
| betreff               | Betreff zum Unterhalt.                    | long description | N         | ''          |
| bisuhrzeit            | Feld für die Uhrzeit bis.                 | text             | Y         |             |
| bkphelement_seqnr     | FK zu bkphelement                         | key              | Y         |             |
| dmsbelegposten_seqnr  | FK zu dmsbelegposten                      | key              | N         |             |
| geraet_seqnr          | FK zu geraet                              | key              | Y         |             |
| geraettyp_seqnr       | FK zu geraettyp                           | key              | Y         |             |
| kosten                | Kosten des Unterhalts.                    | amount           | Y         |             |
| liegenschaft_seqnr    | FK zur Liegenschaft                       | key              | Y         |             |
| mand_seqnr            | FK zum Mandanten                          | key              | N         |             |
| nr                    | Nummer, welche das System vorschlägt.     | ID               | N         | 0           |
| objekt_seqnr          | FK zum Objekt                             | key              | Y         |             |
| person_seqnr          | FK zur Person                             | key              | Y         |             |
| raum                  | Raum, wo die Arbeiten stattfinden.        | text             | N         | ''          |
| statusgueltigab       | Gültigkeitsbeginn des Status.             | date             | Y         |             |
| unterhaltstatus_seqnr | FK zu unterhaltstatus                     | key              | N         |             |
