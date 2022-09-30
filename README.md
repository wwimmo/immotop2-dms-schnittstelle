# immotop2-dms-schnittstelle

- [immotop2-dms-schnittstelle](#immotop2-dms-schnittstelle)
  - [Offene DMS Schnittstelle für das Immobilien-ERP ImmoTop2](#offene-dms-schnittstelle-für-das-immobilien-erp-immotop2)
  - [Generelles](#generelles)
  - [Schnittstellen](#schnittstellen)
  - [Daten lesen und schreiben in ImmoTop2](#daten-lesen-und-schreiben-in-immotop2)
    - [DB Views](#db-views)
    - [DB Prozeduren](#db-prozeduren)
    - [Restservice](#restservice)
  - [Ablauf Kreditorenworkflow](#ablauf-kreditorenworkflow)

## Offene DMS Schnittstelle für das Immobilien-ERP ImmoTop2

Dieses Dokument richtet sich an DMS Hersteller und Implementationspartner. Es enthält die Dokumentation über den Aufbau und Inhalt der universellen DMS Schnittstelle ImmoTop2. Das Dokument dient als Implementationshilfe und Nachschlagewerk für DMS Hersteller und Implementationspartner.

## Generelles
-	Ein Dokument existiert in ImmoTop2 nur ein einziges mal,</br>(entweder im ImmoTop2-internen Archiv oder im externen Archiv eines DMS).
-	Master für die Indexwerte der Dokumente ist ImmoTop2.
-	Das DMS ermöglicht das Viaualisieren von Dokumenten durch Aufruf einer URL mit der DokumentenID als Platzhalter
-	Dokumente werden immer über eine eindeutige DocID identifiziert

## Schnittstellen

<img src="./_images/Uebersicht.jpg" alt="Übersicht" style="float:left; margin-right:10px;" />

Die ImmoTop2-Schnittstellen ermöglichen den DMS:
- lesende und schreibende Zugriffe via <b>[REST-Services](RestService.md)</b>
- lesende Zugriffe via [DatenbankViews](UebersichtViews.md) und schreibende Zugriffe via [Stored-Procedures](EinsatzProzeduren.md) über eine direkte <b>Datenbank-Schnittstelle</b> 
- ausführen von Commands (zB Lösche Dokument 123) über Steuerdateien in <b>Staging-Verzeichnissen</b>

## Daten lesen und schreiben in ImmoTop2

ImmoTop 2 stellt Stammdaten den DMS in [Views](UebersichtViews.md) zur Verfügung.

Das DMS erhält einen Benutzer für lesenden Zugriff. Die Verbindung auf die [Views](UebersichtViews.md) erfolgt mittels ODBC, zusätzlich denkbar wäre auch eine Verbindung mittels ADO.Net, OLE.DB. Ein [REST-Services](RestService.md) steht auch zur Verügung.

### DB Views

Die DV Views sind in folgendem Dokument beschrieben: [Views](UebersichtViews.md)

### DB Prozeduren

Der Aufruf der Prozeduren ist in folgendem Dokument beschrieben: [Prozeduren](EinsatzProzeduren.md)

### Restservice

Verwendung des Webservices wird in diesem Dokument beschrieben: [REST-Services](RestService.md)

## Ablauf Kreditorenworkflow

Der Beleg wird im DMS gescannt.

Der Beleg durchläuft im DMS einen Kreditoren-Workflow.

Metainformationen zum Beleg werden vom DMS ins ImmoTop2 geschrieben. Hierfür werden [Prozeduren](EinsatzProzeduren.md) und ein [REST-Services](RestService.md) zur Verfügung gestellt um die Daten in sogenannte Staging-Tabellen zu schreiben (DmsImport, DmsBeleg und DmsBelegPosten).

In ImmoTop2 wird der Beleg geprüft. Die Daten werden gegebenenfalls ergänzt oder korrigiert und in die Buchhaltung geschrieben.

Die Rechnung wird über ImmoTop2 ausbezahlt.
