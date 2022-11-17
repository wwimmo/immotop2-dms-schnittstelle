# REST-Services

Anstatt direkt mit Views und Prozeduren auf die ImmoTop2 Datenbank zuzugreifen, gibt es auch die Möglichkeit die Daten über REST-Services zu lesen und zu schreiben.
Der 

- [REST-Services](#rest-services)
  - [Einrichten des Webservice im ImmoTop 2](#einrichten-des-webservice-im-immotop-2)
  - [Basisinformationen](#basisinformationen)
    - [Authentisierung](#authentisierung)
    - [Versionierung](#versionierung)
    - [Meldungsformate](#meldungsformate)
  - [Post Methoden](#post-methoden)
    - [SpeichereDmsImport](#speicheredmsimport)
    - [UpdateDmsImport](#updatedmsimport)
    - [UpdateDmsBeleg](#updatedmsbeleg)
    - [UpdateDmsBelegPosten](#updatedmsbelegposten)
  - [Get Methoden](#get-methoden)
    - [Views](#views)
    - [Filterung](#filterung)

## Einrichten des Webservice im ImmoTop 2

In der Datei 'config.ini' im Verzeichnis des ImmoTop2 Server-Prozesses müssen die folgenden beiden Einträge existieren:

| Name des Parameters      | Notwendigkeit | Kommentar                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| :----------------------- | :------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RestServiceUrl           | obligatorisch | Der REST-Service wird nur gestartet, wenn dieser Parameter eine gültige URL enthält.</br>Die Sichtbarkeit im Netzwerk muss gewährleistet sein.<br>URL und Port können frei gewählt werden (der Port darf natürlich noch nicht von einem anderen Prozess belegt sein, sonst kann der REST-Service nicht gestartet werden).<br><br>Wenn konfiguriert wird:<br>RestServiceUrl=http://localhost:8080/ImmoTop2<br>dann kann zB. in Postman mit GET der folgende REST-Service aufgerufen werden http://localhost:8080/ImmoTop2/Test |
| SslCertificateThumbPrint | fakultativ    | Wird benötigt, wenn https benutzt wird.</br>Enthält den Thumbprint des SSL-Zertifikats.<br>Das SSL-Zertifikat muss im Zertifikatspeicher LocalMachine/My des PC geladen sein.</br>Das SSL-Zertifikat wird nicht von W&W geliefert, denn der Commonname sollte ja in die Domain des Kunden integriert sein.<br><br>Wenn der Konfigurationsparameter keinen Wert enthält, sind die REST-Services via http erreichbar.                                                                                                           |

Bei Problemen befinden sich im Logfile 'WwimmoBusinessServer.log' des ImmoTop2-Servers weitere Informationen:
- REST-ServiceHost wurde erfolgreich gestartet...
- REST-ServiceHost wurde nicht gestartet, weil....
- ...

Weil diese Parameter nur sehr selten ändern sollten, wurde die Lösung via 'config.ini' gewählt. Dh. nach dem Aktualisieren dieser Parameter muss der Server-Prozess neu gestartet werden.

## Basisinformationen

### Authentisierung
Die REST-Services benutzen Basic Authentisierung:

- Basic Auth
- User: wwdms
- Passwort wird von W&W geliefert

### Versionierung
Alle REST-Services sind versioniert, damit der ImmoTop2-Server-Service verschiedene DMS-Versionen unterstützen zu können.
Deshalb muss Request des REST-Services der Header Version vorhanden sein:

- Version:  1.0

### Meldungsformate
Request und Response werden im JSON-Format erwartet und zurück geliefert.

## Post Methoden

### SaveDmsImport

*Request:*

```json
{
    "DmsArchivGuid": "f1234f8d81044c9a8a262c4b7d8a07b3",
    "DmsDocumentGuid": "",
    "DmsDocumentId": 123123124,
    "DmsDateiName": "dummy_2022.06.14_08_50:25.pdf",
    "dmsimportfehlercode_seqnr": null,
    "dmsimportstatus_seqnr": 1,
    "dmsinsts": "2022-06-14T00:00:00",
    "dmsinsusr": "ASE",
    "dmsupdatets": "2022-06-14T00:00:00",
    "dmsupdateusr": "ASE",
    "DmsBeleg": {
        "BelegArtNr": 1,
        "BelegDatum": "2022-06-14T00:00:00",
        "belegcode_seqnr": 302,
        "BelegNummer": "123",
        "BenoetigtGeraetEintrag": false,
        "BenoetigtUnterhaltEintrag": false,
        "BuchungDatum": "2022-06-14T00:00:00",
        "EsrReferenzNummer": "955318100004910058518606215",
        "HatZahlungSperre": false,
        "kreditor_seqnr": 157,
        "KreditorCo": "",
        "KreditorGeschlechtNummer": null,
        "KreditorLand": "",
        "kreditormwstnr_seqnr": "",
        "KreditorName": "",
        "KreditorPlz": "",
        "KreditorPostfach": "",
        "KreditorStrasse": "",
        "KreditorVorname": "",
        "KreditorZahlstelleKontoDetail": "",
        "mand_seqnr": 3,
        "QrCodePayload": "",
        "RechnungNummer": "",
        "zahlstellekreditor_seqnr": 4866,
        "zahlstellemandant_seqnr": null,
        "ZahlungGrund": "",
        "ZahlungKonditionFaelligkeit": 30,
        "ZahlungKonditionFaelligPerDatum": null,
        "DmsBelegPosten": [
            {
                "BetragBrutto": 12345.65,
                "BetragExklMwst": null,
                "BetragMwstVoll": null,
                "BuchungText": "TestImport_14.06.2022 08:50:25",
                "FaelligkeitDatum": "2022-07-14T00:00:00",
                "konto_seqnr": 74,
                "kostenstelle_seqnr": 6,
                "mahnungtyp_seqnr": 11,
                "Menge": null,
                "mwstabrechnungziffer_seqnr": null,
                "mwstcode_seqnr": null,
                "MwstSatz": null,
                "NkabrechnungPeriodeStichtag": null,
                "Nr": 1,
                "PreisProEinheit": null,
                "VorsteuerAnteil": null
            },
            {
                "BetragBrutto": 12345.65,
                "BetragExklMwst": null,
                "BetragMwstVoll": null,
                "BuchungText": "TestImport_14.06.2022 08:50:25",
                "FaelligkeitDatum": "2022-07-14T00:00:00",
                "konto_seqnr": 74,
                "kostenstelle_seqnr": 6,
                "mahnungtyp_seqnr": 11,
                "Menge": null,
                "mwstabrechnungziffer_seqnr": null,
                "mwstcode_seqnr": null,
                "MwstSatz": null,
                "NkabrechnungPeriodeStichtag": null,
                "Nr": 2,
                "PreisProEinheit": null,
                "VorsteuerAnteil": null
            }
        ]
    }
}
```

*Response:*

```json
{
    "Erfolgreich": true,
    "FehlerCode": 0,
    "FehlerMeldung": null,
    "import_seqnr": 778193,
    "beleg_seqnr": 778193,
    "BelegPostenList": [
        {
            "s_seqnr": 36114,
            "nr": 1
        },
        {
            "s_seqnr": 36115,
            "nr": 2
        }
    ]
}
```
 
### UpdateDmsImport

*Request:*

```json
{
    "s_seqnr": 778193,
    "DmsArchivGuid": "f1234f8d81044c9a8a262c4b7d8a07b3",
    "DmsDocumentGuid": "",
    "DmsDocumentId": 1234600,
    "DmsDateiName": "dummy_2022.06.14_08_50:25.pdf",
    "DmsImportFehlerCode": null,
    "DmsImportStatusCode": 1,
    "dmsimportstatus_seqnr": 1,
    "dmsinsts": "2022-06-14T00:00:00",
    "dmsinsusr": "ASE",
    "dmsupdatets": "2022-06-14T00:00:00",
    "dmsupdateusr": "ASE"
}
```

*Response:*

```json
{
    "Erfolgreich": true,
    "FehlerCode": 0,
    "FehlerMeldung": null,
    "import_seqnr": 778193
}
```

### UpdateDmsBeleg

*Request:*

```json
{
    "s_seqnr": 900842,
    "BelegArtNr": 1,
    "BelegDatum": "2022-06-14T00:00:00",
    "belegcode_seqnr": 302,
    "BelegNummer": "",
    "BenoetigtGeraetEintrag": false,
    "BenoetigtUnterhaltEintrag": false,
    "BuchungDatum": "2022-06-14T00:00:00",
    "EsrReferenzNummer": "955318100004910058518606215",
    "HatZahlungSperre": false,
    "dmsimport_seqnr": 901121,
    "kreditor_seqnr": 157,
    "KreditorCo": "",
    "KreditorGeschlechtNummer": null,
    "KreditorLand": "",
    "KreditorMwstNummer": "",
    "KreditorName": "",
    "KreditorPlz": "",
    "KreditorPostfach": "",
    "KreditorStrasse": "",
    "KreditorVorname": "",
    "KreditorZahlstelleKontoDetail": "",
    "mand_seqnr": 3,
    "QrCodePayload": "",
    "RechnungNummer": "",
    "zahlstellekreditor_seqnr": 4866,
    "zahlstellemandant_seqnr": null,
    "ZahlungGrund": "",
    "ZahlungKonditionFaelligkeit": 30,
    "ZahlungKonditionFaelligPerDatum": null
}
```

*Response:*

```json
{
    "Erfolgreich": true,
    "FehlerCode": 0,
    "FehlerMeldung": null,
    "beleg_seqnr": 778193
}
```

### UpdateDmsBelegPosten

*Request:*

```json
{
    "s_seqnr": 49648,
    "BetragBrutto": 12345.65,
    "BetragExklMwst": null,
    "BetragMwstVoll": null,
    "BuchungText": "TestImport_14.06.2022 08:50:25",
    "dmsbeleg_seqnr": 900842,
    "FaelligkeitDatum": "2022-07-14T00:00:00",
    "konto_seqnr": 74,
    "kostenstelle_seqnr": 6,
    "mahnungtyp_seqnr": 11,
    "Menge": null,
    "mwstabrechnungziffer_seqnr": null,
    "mwstcode_seqnr": null,
    "MwstSatz": null,
    "NkabrechnungPeriodeStichtag": null,
    "Nr": 1,
    "PreisProEinheit": null,
    "VorsteuerAnteil": null
}
```

*Response:*

```json
{
    "Erfolgreich": true,
    "FehlerCode": 0,
    "FehlerMeldung": null,
    "belegposten_seqnr": 36115
}
```

## Get Methoden

In allen Get Methoden wird kein Body übergeben. Dieser Aufruf besteht nur aus dem Header und optional mit einem Param.

Beispiel Aufruf: https://localhost:8080/GetDmsImportFehlerCodes

### Views

Für jede View gibt es eine passende Get Methode:

| Methode                                  | Bemerkung                                                                                                                    |
| :--------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------- |
| GetDmsImportFehlerCodes                  | v_DmsImportFehlerCode                                                                                                        |
| GetDmsImportStatus                       | v_DmsImportStatus                                                                                                            |
| GetDmsMandant                            | v_DmsMandant                                                                                                                 |
| GetDmsMandantZahlstelle                  | v_DmsMandantZahlstelle                                                                                                       |
| GetDmsKreditor                           | v_DmsKreditor                                                                                                                |
| GetDmsKreditorZahlstelle                 | v_DmsKreditorZahlstelle                                                                                                      |
| GetDmsKonto                              | v_DmsKonto                                                                                                                   |
| GetDmsExportKonto                        | v_DmsExportKonto                                                                                                             |
| GetDmsKontoKostenstelleTyp               | v_DmsKontoKostenstelleTyp                                                                                                    |
| GetDmsKontoKostenstelle                  | v_DmsKontoKostenstelle                                                                                                       |
| GetDmsKostenstelle                       | v_DmsKostenstelle                                                                                                            |
| GetDmsExportKostenstelle                 | v_DmsExportKostenstelle                                                                                                      |
| GetDmsMwstAbrechnungZiffer               | v_DmsMwstAbrechnungZiffer                                                                                                    |
| GetDmsVorsteuerAnteil                    | v_DmsvorsteuerAnteil                                                                                                         |
| GetDmsKostenGruppeKostenKonto            | v_DmsKostenGruppeKostenKonto                                                                                                 |
| GetDmsMahnungTyp                         | v_DmsMahnungTyp                                                                                                              |
| GetDmsMwstCode                           | v_DmsMwstCode                                                                                                                |
| GetDmsMwstSatz                           | v_DmsMwstSatz                                                                                                                |
| GetDmsAbrechnungPeriode                  | v_DmsAbrechnungPeriode                                                                                                       |
| GetDmsBelegCode                          | v_DmsBelegCode                                                                                                               |
| GetDmsObjekt                             | v_DmsObjekt                                                                                                                  |
| GetDmsMieter                             | v_DmsMieter                                                                                                                  |
| GetDmsVerhaeltnis                        | v_DmsVerhaeltnis                                                                                                             |
| GetDmsCode                               | v_DmsCode                                                                                                                    |
| GetDmsLiegenschaft                       | v_DmsLiegenschaft                                                                                                            |
| GetDmsLiegenschaftGruppeNebenkosten      | v_DmsLiegenschaftGruppeNebenkosten                                                                                           |
| GetDmsBuchungDokument                    | v_DmsBuchungDokument                                                                                                         |
| GetDmsMitarbeiter                        | v_DmsMitarbeiter                                                                                                             |
| GetDmsBelegzahlungAngaben                | v_DmsBelegzahlungAngaben                                                                                                     |
| GetDmsZahlungposten                      | v_DmsZahlungposten                                                                                                           |
| GetDmsImport                             | Tabelle DmsImport                                                                                                            |
| GetDmsBeleg                              | Tabelle DmsBeleg                                                                                                             |
| GetDmsBelegPosten                        | Tabelle DmsBelegPosten                                                                                                       |
| GetDmsImportById                         | Aufruf: GetDmsImportById?Id=715271</br>Liefert DmsImport, DmsBeleg und DmsBelegPosten mit der angegebenen Id des DmsImports. |
| GetDmsDokumentIndexFelderByDmsDocumentId | Aufruf: GetDmsDokumentIndexFelderByDmsDocumentId?DmsDocumentId=1000064466                                                    |

### Filterung

_ab Version 2.6.23_

Grundsätzlich ist es möglich nach allen Spalten zu Filtern. Wenn man zum Beispiel allen Konten eines bestimmten Mandanten finden will, sieht der Aufruf so aus:

http://localhost:8080/GetDmsKonto?mandant_seqnr=3

Jede zusätzliche Spalte wird mit einem & verknüpft:

http://localhost:8080/GetDmsKonto?mandant_seqnr=3&nebenbuchtypnr=2
