# v_DmsBudgetPerHeute
Ermittelt das Budget für das aktuelle Tagesdatum (NOW()).<br>
Falls die View keinen Rückgabewert liefert, ist kein Budget vorhanden.<br>
Wenn man bei einem Konto mit Kostenstellen das Budget des Kontos alleine berechnen möchte , muss das mit SUM() berechnet werden.

_Verfügbar ab Version 2.7.24_

## Tabelle
| Name               | Kommentar                                                       | Datentyp | Länge | Nullable |
| :----------------- | :-------------------------------------------------------------- | :------- | ----: | :------: |
| mandant_seqnr      | Id des Mandanten                                                | long     |    64 |    N     |
| kontonr            | Kontonummer                                                     | varchar  |    20 |    N     |
| konto_seqnr        | Id des Kontos                                                   | long     |    64 |    N     |
| kostenstelle_seqnr | Id der Kostenstelle                                             | long     |    64 |    Y     |
| budget             | Budget per aktuellem Datum                                      | decimal  |       |    N     |
| buch               | Buchbezeichnung:<br>Hauptbuch<br>Debitoren<br>Kapital<br>Kosten | varchar  |     9 |    N     |