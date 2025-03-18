# Theorie Tag 5

## Löschen von Daten in professionellen Datenbank

- Üblicherweise ist der Lösch-Befehl "delete" in professionellen Datenbanken nicht erlaubt
    - Wieso?
		- Dieser Befehl würde zu starkem Datenverlust führen
- Was passiert beim ausführen dieses Befehls:
    - Wenn ich zum Beispiel einen Mitarbeiter aus einer Tabelle löschen will und den Befehl "delete" dafür verwende, dann verschwindet nicht nur der Datensatz des Mitarbeiters, sondern auch alle Beziehungen, welche mit dem Mitarbeiter in Verbindung standen
        - Wenn das passiert, dann kann man von der Datenbank aus nicht mehr verstehen, welche Position und Beziehungen dieser Mitarbeiter zuvor hatte. Welchen Job er hatte, ob er eine Führungsposition oder -beziehung hatte und viel mehr.
            - Bzw. viele Aktivitäten wären nicht mehr nachvollziehbar -> kann auch zu juristischen Problemen führen
- Was kann man tun:
    - Als Lösung kann man z.B. den Datensatz nciht löschen, sondern umgekehrt erweitern und zum Beispiel als inaktiv markieren
        - Kann aber redundant sein
- Das Problem mit dem Update Befehl:
    - Zeitliche Abläufe kann man auch nicht einfach überschreiben.
    - Wenn man z.B. einen Gegenstand hat, welcher nach und nach an andere Leute verliehen wird kann in so einem Fall nicht nur einen Fremdschlüssel haben. Wenn er nur einen Fremdshclüssel hätte, so würde dieser zwar auf die Personen, welche ihn mal hatten oder zurzeit haben zeigen, daraus könnte man aber keine zeitlichen Abläufe herausfinden.
    - Hier würde man zusätzliche Tabellen benötigen, um die zeitlichen Abläufe zu dokumentieren. Damit kann man auch Aussagen über die zeitlichen Abläufe aussagen.

- Kassenbeispiel:
    - Man stellt sich hier vor, dass man einkaufen geht, den Einkauf beginnt, zur Kasse geht und erst nachdem der Kassierer alle Artikel gescannt und die Einträge in der Datenbank gespeichert hat, merkt man, dass man zu wenig Geld hat.
        - In einem solchen Fall müsste man ja die Datensätze löschen
            - Dieses Verhalten könnte aber sehr einfach missbraucht werden und somit kann man dies nicht erlauben
            - Stattdessen kann man diese Daten in einer neuen Tabelle abspeichern:
                - Die neue Tabelle "Stornierungen" kann man mit neuen Daten erweitern. Was wurde storniert, wieso, wann usw.

- Allgemein:
    - Anstelle des Löschen von Daten, was zu komplizierten Verständnis oder juristischen Problemen führen kann, kann man stattdessen die Datenbank mit weiteren Tabellen, welche spezielle Informationen haben erweitern. Somit erweitert man datensätze und beschrebt diese neu anstelle sie zu löschen.
 
## Datenintegrität

Datenintergrität = Korrektheit, Konsistenz und Vertrauenswürdigkeit von Daten innerhalb einer Datenbank

1. Eindeutigeit und Datenkonsistenz:
    - Jeder Datensatz muss eindeutig identifizeirbar sein und für eine lange Zeit bestehen
          - Ihr Zustand soll nicht ungewollt geändert werden können
          - Redundazen sollen somit verhindert werden

2. Referenzielle Integrität:
    - Wenn Tabellen in Beziehung zueindander stehen, sollen diese Beziehungen immer konsistent beliben
         - Beziehungen können nur dann bestehen, wenn beide Datensätze wirklich existieren

3. Datentypen:
    - Daten sollen immer mit ihren richtigen Datentyp gespeichert werden
          - Vermeidung von Fehlern

4. Datenbeschränkung:
    - Nur gültige Daten sollen in die Datenbank eingefügt werden können
    - z.B sollen nur positive Zahlen eingefügt werden oder eine Email soll in ebstimmten Format entsprechen

5. Validierung:
    - Vor dem Einfügen von Daten, muss man zuers die Datenbank validieren
          - Das heisst, überprüfen, ob die Daten in der Datenbank korrekt sind. Nur wenn alle Daten stimmen darf man neue Daten einfügen.
               - Wird dies nicht gemacht, so kann es zu komplizierten Fehlern kommen, welche nur mit grossem Zeitaufwand korrigiert werden können
          

## Fremdschlüssel-Regeln beim Löschen

Als Beispiel stellt man sich vor, dass man einen Foreign Key-Constraint haben und dann einen Datensatz in der Primärtabelle wird. Um die gewolte Aktion in solchen Fällen zu erhalten gibt es einige Befehle/Einstelungen, die ON DELETE-Regeln:

- NO ACTION:
    - Standartverfahren
        - Muss nicht angegeben werden
    - Normalle Delete, heir können also Daten nur dann aus der Primärtabelle gelöscht werden, wenn in keiner Zusatz- oder Detail-Tabelle Daten mit demselben Wert existieren. Also wenn dieser Wer noch irgendwo gebraucht wird, dann wird dieser Befehl nicht ausgeführt
          - Wenn ich einen Primärschlüssel löschen will, aber dieser in der z.B. Kundentabelle noch gebraucht wird

- CASCADE:
    - Mit diesem Befehl werden die Daten der Primärtabelle welche gelöscht werden gleichzeitig auch in allem anderen Tabellen gelöscht.
        - Wenn ich den Primärschlüssel Kunde = 1, und alle seinen Werte löschen will, werden mit dem CASCASE BEfehl alle Datensätze, wo der Primärschlüssel Kunde = 1 als Fremdschlüssel verwendet werden auch gelöscht.
    - mit diesem Befehl muss man aber darauf achten, dass unabsichtlich falsche Daten gelöscht werden können
- SET NULL:
    - Hier werden alle Datensätze , welche in der Primärtabelle gelöscht werden, in den Fremschlüsseltabellen auf NULL gesetzt.
        - Wenn ch den Primärschlüssel Kunde = 2 und dessen Daten in der Primärtabelle löschen will, dann werden automatisch alle Datensätze in den Fremdschlüsseltabellen, welche diese Daten nutzen auf NULL gesetzt.
    - Funktioniert nur bei c:m oder c:c Beziehungen -> wenn beim Fremdschlüssel der Wert NULL erlaubt ist
    - DEFAULT:
		- falls man einen Default-Wert definiert, so wird dieser in die Fremdschlüsseltabellen eingesetzt statt der Wert NULL


- Beispiel:

  ```
  CREATE TABLE IF NOT EXISTS kunden (
      ID_Bestellung int NOT NULL AUTO_INCREMENT,
      Beschreibung VARCHAR(100) NOT NULL,
      Kunden_ID int,
      PRIMARY KEY(ID_Bestellung),
      CONSTRAINT fk_kunden
          FOREIGN KEY (Kunden_ID)
          REFERENCES kunden(ID_Kunden)
          ON DELETE NO ACTION ON UPDATE CASCADE
  );
  ```
      

## SELECT ALIAS

  ALIAS = temporäre Name

- Spalten:
    - In SQL kann man Spalten temporäre Namen geben, welche für die bessere und verständlichere Ansicht nutzbar sind.
      ```
      SELECT name FROM Kunden AS "last name";
      ```
        - Hier wird die Splate "name" temporär als "lastname" gezeigt
- Tabellen:
    - Man kann auch Tabellen einen ALIAS geben, welcher nutzbar wird, wenn man Daten aus verschiedenen Tabellen in einem Befehl aufruft. Um nicht vor jeder Spalte den ganzen Namen der gewünschten Tabelle einzugeben, kan man im Befehl der Tabelle einen neuen temporären Namen geben
      ```
      SELECT k.Name, b.Beschreibung
      FROM kunden k
      JOIN bestellungen b ON k.ID_Kunde = b.Kunden_ID
      WHERE k.Name = 'Max Mustermann';
      ```

## Aggregatsfunktionen

### Count() 
- Zählt Anzahl an Einträge
- Hier kann man auch einfach * statt splate benutzen, wenn in die spalte ganz ausgefüllt ist
    - Anzahl aller Datensätze
    - Wenn man spezifische Spalte eingibt, werden nur die Anzahl Werte ohne NULL Werte angezeigt
- SELECT COUNT(city) FROM location;
- 
### Max()
- Höchste Wert einer Spalte wird angezeigt
- SELECT MAX(salary) FROM employee;
- Bei STRING -> es sucht nach dem alpahbetischen Prinzip

### Min()
- Tiefste/kleinste Wert einer Splate wird angezeigt
- SELECT MIN(salary) FROM employee;
- Bei STRING -> es sucht nach dem alpahbetischen Prinzip
  
### AVG()
- Berechnet den Durchschnitt einer Spalte
- SELECT AVG(salary) FROM employee;

### SUM()
- Berechnet die SUMME der Werte in einer Spalte oder Gruppe
- SELECT SUM(salary) FROM employee;


## Merksatz

"Sag Fritz, warum geht Herbert oft laufen?"

- S -> SELECT + column-name
- F -> FROM + table-name
- W -> WHERE + condition
- G -> GROUP BY + column-name
- H -> HAVING + condition
- O -> ORDER BY + column-name


## GROUP BY

- Wird mir Aggregatsfunktionen verwendet
- Daten werden in Gruppen zusammengefasst und gruppiert
- Zeilen mit demselben Wert (in der Gruppenspalte) werden in einer Gruppe zusammengefasst
- BSP:
```
		SELECT product_id, SUM(amount) AS total_sales
		FROM sales
		GROUP BY product_id;
```
- Hier bekommt man für jede product_id die Ausgaben von amount zusammengerechnet
	- Gesamme Verkaufssumme pro product_id wird berechnet
- Mit group by kann man werte nach einem kriterium gruppieren


## HAVING

- HAVING ist der Befehl, um Ergebnisse von GROUP BY zu filtern
- HAVING-Klausel wird auf die aggregierten Ergebnisse nach der Gruppierung angewendet
- BSP:

```
	SELECT MAX(salary), id_department 
	FROM employee 
	GROUP BY id_department
	HAVING MAX(salary) > 12000;

```
- Hier werden also nur die Resultate der GROUP BY angezeigt, welche den Wert > 12000 haben
