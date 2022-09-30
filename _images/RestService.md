# REST-Services

Anstatt direkt mit Views und Prozeduren auf die ImmoTop2 Datenbank zuzugreifen, gibt es auch die Möglichkeit die Daten über REST-Services zu lesen und zu schreiben.
Der 

- [Webservice](#webservice)
  - [Einrichten des Webservice im ImmoTop 2](#einrichten-des-webservice-im-immotop-2)
  - [Basisinformationen](#basisinformationen)
  - [Post Methoden](#post-methoden)
    - [SpeichereDmsImport](#speicheredmsimport)
    - [UpdateDmsImport](#updatedmsimport)
    - [UpdateDmsBeleg](#updatedmsbeleg)
    - [UpdateDmsBelegPosten](#updatedmsbelegposten)
  - [Get Methoden](#get-methoden)

## Einrichten des Webservice im ImmoTop 2

Im config.ini des ImmoTop2 Server müssen die folgenden beiden Einträge existieren:

|                          |               |                                                                                                                                                                                                                       |
| :----------------------- | :------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RestServiceUrl           | obligatorisch | Der REST-Service wird nur gestartet, wenn dieser Parameter eine gültige URL enthält.</br>Die Sichtbarkeit im Netzwerk muss gewährleistet und der CommonName des fakultativen Zertifikats muss mit der URL übereinstimmen. |
| SslCertificateThumbPrint | fakultativ    | Wird benötigt, wenn https benutzt wird.</br>Das SSL-Zertifikat muss im Zertifikatspeicher LocalMachine/My des PC geladen sein.</br>Das SSL-Zertifikat wird nicht von W&W geliefert (muss in Domain des Kunden integriert sein)                                                                                |

Bei Problemen befinden sich im Logfile 'WwimmoBusinessServer.log' des ImmoTop2-Servers weitere Informationen:
- REST-ServiceHost wurde erfolgreich gestartet...
- REST-ServiceHost wurde nicht gestartet, weil....
- ...

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

### SpeichereDmsImport

*Request:*

```json
{
    "DmsArchivGuid": "f1234f8d81044c9a8a262c4b7d8a07b3",
    "DmsDocumentGuid": "",
    "DmsDocumentId": 1234698,
    "DmsDateiName": "dummy_2022.06.14_08_50:25.pdf",
    "DmsImportFehlerCode": null,
    "DmsImportStatusCode": 1,
    "DmsImportStatusId": 1,
    "DmsInsertedTs": "2022-06-14T00:00:00",
    "DmsInsertedUser": "ASE",
    "DmsUpdateTs": "2022-06-14T00:00:00",
    "DmsUpdateUser": "ASE",
    "DmsBeleg": {
        "BelegArtNummer": 1,
        "BelegDatum": "2022-06-14T00:00:00",
        "BelegCodeId": 32,
        "BelegNummer": "",
        "BenoetigtGeraetEintrag": false,
        "BenoetigtUnterhaltEintrag": false,
        "BuchungDatum": "2022-06-14T00:00:00",
        "EsrReferenzNummer": "955318100004910058518606215",
        "HatZahlungSperre": false,
        "KreditorId": 157,
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
        "MandantId": 3,
        "QrCodePayload": "",
        "RechnungNummer": "",
        "ZahlstelleKreditorId": 4866,
        "ZahlstelleMandantId": null,
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
                "KontoId": 74,
                "KostenstelleId": 6,
                "MahnungTypId": 11,
                "Menge": null,
                "MwstAbrechnungZifferId": null,
                "MwstCodeId": null,
                "MwstSatz": null,
                "NkabrechnungPeriodeStichtag": null,
                "Nummer": 1,
                "PreisProEinheit": null,
                "VorsteuerAnteil": null
            },
            {
                "BetragBrutto": 12345.65,
                "BetragExklMwst": null,
                "BetragMwstVoll": null,
                "BuchungText": "TestImport_14.06.2022 08:50:25",
                "FaelligkeitDatum": "2022-07-14T00:00:00",
                "KontoId": 74,
                "KostenstelleId": 6,
                "MahnungTypId": 11,
                "Menge": null,
                "MwstAbrechnungZifferId": null,
                "MwstCodeId": null,
                "MwstSatz": null,
                "NkabrechnungPeriodeStichtag": null,
                "Nummer": 2,
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
    "ImportId": 778193,
    "BelegId": 778193,
    "BelegPostenList": [
        {
            "Id": 36114,
            "Nummer": 1
        },
        {
            "Id": 36115,
            "Nummer": 2
        }
    ]
}
```
 
### UpdateDmsImport

*Request:*

```json
{
    "Id": 778193,
    "DmsArchivGuid": "f1234f8d81044c9a8a262c4b7d8a07b3",
    "DmsDocumentGuid": "",
    "DmsDocumentId": 1234600,
    "DmsDateiName": "dummy_2022.06.14_08_50:25.pdf",
    "DmsImportFehlerCode": null,
    "DmsImportStatusCode": 1,
    "DmsImportStatusId": 1,
    "DmsInsertedTs": "2022-06-14T00:00:00",
    "DmsInsertedUser": "ASE",
    "DmsUpdateTs": "2022-06-14T00:00:00",
    "DmsUpdateUser": "ASE"
}
```

*Response:*

```json
{
    "Erfolgreich": true,
    "FehlerCode": 0,
    "FehlerMeldung": null,
    "ImportId": 778193
}
```

### UpdateDmsBeleg

*Request:*

```json
{
    "Id": 778193,
    "BelegArtNummer": 1,
    "BelegDatum": "2022-06-14T00:00:00",
    "BelegCodeId": 32,
    "BelegNummer": "",
    "BenoetigtGeraetEintrag": false,
    "BenoetigtUnterhaltEintrag": false,
    "BuchungDatum": "2022-06-14T00:00:00",
    "EsrReferenzNummer": "955318100004910058518606215",
    "HatZahlungSperre": false,
    "DmsImportId": 778193,
    "KreditorId": 157,
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
    "MandantId": 3,
    "QrCodePayload": "",
    "RechnungNummer": "",
    "ZahlstelleKreditorId": 4866,
    "ZahlstelleMandantId": null,
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
    "BelegId": 778193
}
```

### UpdateDmsBelegPosten

*Request:*

```json
{
    "Id": 36115,
    "BetragBrutto": 12345.25,
    "BetragExklMwst": null,
    "BetragMwstVoll": null,
    "BuchungText": "TestImport_14.06.2022 08:50:25",
    "DmsBelegId": 778193,
    "FaelligkeitDatum": "2022-07-14T00:00:00",
    "KontoId": 74,
    "KostenstelleId": 6,
    "MahnungTypId": 11,
    "Menge": null,
    "MwstAbrechnungZifferId": null,
    "MwstCodeId": null,
    "MwstSatz": null,
    "NkabrechnungPeriodeStichtag": null,
    "Nummer": 2,
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
    "BelegPostenId": 36115
}
```

## Get Methoden

In allen Get Methoden wird kein Body übergeben. Dieser Aufruf besteht nur aus dem Header und optional mit einem Param. Beispiel Aufruf: https://localhost:8080/GetDmsImportFehlerCodes

Für jede View gibt es eine passende Get Methode:

| Methode                             | Bemerkung                                                                                                                    |
| :---------------------------------- | :--------------------------------------------------------------------------------------------------------------------------- |
| GetDmsImportFehlerCode              | v_DmsImportFehlerCode                                                                                                        |
| GetDmsImportStatus                  | v_DmsImportStatus                                                                                                            |
| GetDmsMandant                       | v_DmsMandant                                                                                                                 |
| GetDmsMandantZahlstelle             | v_DmsMandantZahlstelle                                                                                                       |
| GetDmsKreditor                      | v_DmsKreditor                                                                                                                |
| GetDmsKreditorZahlstelle            | v_DmsKreditorZahlstelle                                                                                                      |
| GetDmsKonto                         | v_DmsKonto                                                                                                                   |
| GetDmsExportKonto                   | v_DmsExportKonto                                                                                                             |
| GetDmsKontoKostenstelleTyp          | v_DmsKontoKostenstelleTyp                                                                                                    |
| GetDmsKontoKostenstelle             | v_DmsKontoKostenstelle                                                                                                       |
| GetDmsKostenstelle                  | v_DmsKostenstelle                                                                                                            |
| GetDmsExportKostenstelle            | v_DmsExportKostenstelle                                                                                                      |
| GetDmsMwstAbrechnungZiffer          | v_DmsMwstAbrechnungZiffer                                                                                                    |
| GetDmsVorsteuerAnteil               | v_DmsvorsteuerAnteil                                                                                                         |
| GetDmsKostenGruppeKostenKonto       | v_DmsKostenGruppeKostenKonto                                                                                                 |
| GetDmsMahnungTyp                    | v_DmsMahnungTyp                                                                                                              |
| GetDmsMwstCode                      | v_DmsMwstCode                                                                                                                |
| GetDmsMwstSatz                      | v_DmsMwstSatz                                                                                                                |
| GetDmsAbrechnungPeriode             | v_DmsAbrechnungPeriode                                                                                                       |
| GetDmsBelegCode                     | v_DmsBelegCode                                                                                                               |
| GetDmsObjekt                        | v_DmsObjekt                                                                                                                  |
| GetDmsMieter                        | v_DmsMieter                                                                                                                  |
| GetDmsVerhaeltnis                   | v_DmsVerhaeltnis                                                                                                             |
| GetDmsCode                          | v_DmsCode                                                                                                                    |
| GetDmsLiegenschaft                  | v_DmsLiegenschaft                                                                                                            |
| GetDmsLiegenschaftGruppeNebenkosten | v_DmsLiegenschaftGruppeNebenkosten                                                                                           |
| GetDmsBuchungDokument               | v_DmsBuchungDokument                                                                                                         |
| GetDmsMitarbeiter                   | v_DmsMitarbeiter                                                                                                             |
| GetDmsBelegzahlungAngaben           | v_DmsBelegzahlungAngaben                                                                                                     |
| GetDmsZahlungposten                 | v_DmsZahlungposten                                                                                                           |
| GetDmsImport                        | Tabelle DmsImport                                                                                                            |
| GetDmsBeleg                         | Tabelle DmsBeleg                                                                                                             |
| GetDmsBelegPosten                   | Tabelle DmsBelegPosten                                                                                                       |
| GetDmsImportById                    | Aufruf: GetDmsImportById?Id=715271</br>Liefert DmsImport, DmsBeleg und DmsBelegPosten mit der angegebenen Id des DmsImports. |
