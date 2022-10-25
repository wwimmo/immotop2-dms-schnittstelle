# Integration in SQL Server

Der direkte Zugang von einem SQL-Server zu Anywhere17-Datenbankobjekten in der von ImmoTop2 benutzten Anywehre17-Datenbank ist über das Feature "Microsoft Linked Server" möglich.


## Installations-Vorgehen:
- Interaktive Installation 
  (siehe Kap 1.4.6.1  im Dokument [SQL-Anywhere-Server-Programming](https://help.sap.com/doc/9457f880abbe4bc8bebc18109daae0ca/17.0/en-US/SQL-Anywhere-Server-Programming-en.pdf) )

- Installation über einen Script
  (siehe Kap 1.4.6.2 im Dokument [SQL-Anywhere-Server-Programming](https://help.sap.com/doc/9457f880abbe4bc8bebc18109daae0ca/17.0/en-US/SQL-Anywhere-Server-Programming-en.pdf))

Bei den Optionen müssen "RPC", "RPC Out"  und "Allow Inprocess" aktiviert sein.
Alle anderen Optionen können ignoriert werden.

## SQL Syntax
Über den OLE-DB Provider kann für die SQL-Statements genutzt werden:
- Openquery-Syntax: Das zweite SQL-Statement wird durchgereicht<br>
  SELECT * FROM OPENQUERY( SADATABASE, 'SELECT * FROM Customers' )
- Microsoft four-part table referencing syntax<br>
  SELECT * FROM SADATABASE.demo.GROUPO.Customers

## Unterstützte OLE DB Interfaces
Das OLE DB API bestehet aus einem Set von interfaces 
[Beschreibung der unterstützten Interfaces](https://help.sap.com/docs/SAP_SQL_Anywhere/98ad9ec940e2465695685d98e308dff5/3bd9bd526c5f1014b15da1ec5a67c8c9.html?locale=en-US&version=17.0&q=linked%20server)

oder

siehe Kap 1.4.7. im Dokument [SQL-Anywhere-Server-Programming](https://help.sap.com/doc/9457f880abbe4bc8bebc18109daae0ca/17.0/en-US/SQL-Anywhere-Server-Programming-en.pdf)