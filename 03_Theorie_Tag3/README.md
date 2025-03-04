# Theorie Tag 3

## Mehrfachbindungen

- Mehrfachbindungen = Tabellen können mehrere unterschiedliche Beziehungen zu einer andere Tabelle haben.
  - z.B Tabelle Fahrt und Tabelle Ort
      - Haben 2 verschiedene Beziehungen zueinander, z.B 1:1 und 1:n
- Damit man die Tabellen nicht verwechselt, muss man die Beziehungen gut durch eine Rolle beschriften
- Rolle = Funktionsbeschreibungen oder Bedeutung einer Beziehung
- Die Kardinalitäten der verschiedenen Beziehungen können auch unterschiedlich sein


## Rekursion

- Rekursion = ein Datensaz einer Tabelle ist mit einem anderen Datensatz aus derselben Tabelle verbunden (steht in Bezihung dazu)
- WIe = Die Tabelle enthält einen Fremdschlüssel, welcher auf den Primärschlüssel der eigenen Tabelle zeigt


 ## Einfache Hierarchie

 - Bei einer Netzwerkstruktur gibt es eine many-many Beziehung (m:n), wobei aber ein ELement gleichzeitig mehrere Rollen einnehmen kann
  - z.B Mitarbeiter hat Rolle "Vorgesetzter" und Rolle "Mitarbeiter"
- Um diese Beziehung zu zeigen braucht man eine Transformationstabelle mit zwei Fremdschlüsseln, welche auf denselben Primärschlüssel zeigen. Diese 2 sollen aber unterrschiedliche Rollen haben.











## Codes

### DDL

#### CREATE

- CREATE TABLE newTable (ID integer, Name varchar(25));

#### DROP

- Tabelle löschen
- DROP TABLE newTAble

#### ALTER 

- Tabelle anpassen (neue Reihen einfügen)
- ALTER TABLE newTABLE ADD COLUMN Vorname varchar(25);



### DML

#### INSERT

- Neue Daten einfüge (neue Spalten)
- INSERT INTO newTable (ID, Name) VALUES (1, 'muster');

#### UPDATE

- Daten anpassen -> In vorhandene Spalte Daten einfügen
- UPDATE newTable SET Name = 'max' WHERE ID = 1;

#### DELETE 

- Spalte löschen (Where = welche spalte)
- DELETE FROM newTable WHERE ID=1;



### DQL

#### SELECT

- SELECT * FROM newTable;
  - Alles anzeigen
- SELECT ID FROM newTable;
  - nur ID anzeigen
