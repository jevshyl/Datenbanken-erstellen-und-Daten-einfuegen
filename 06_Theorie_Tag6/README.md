# Theorie Tag 6

## Subquery

### Was ist ein Subquery/Subselect?

- Ein Subselect = eine ABfrabe innerhalb einer Abfrage
    - SELECT in einem SELECT
- Verwendung
  - um Daten aus einer Tabelle aufzurufen, welche bestimmte Bestimmungen erfüllen, die auf eine andere Tabelle basieren
  - in verschiedenen Stellen innerhalb einer SQL-Abfrage
      - in einer WHERE, FROM, HAVING und SELECT Klausel
      - als Teil einer Anweisung -> UPDATE, DALETE, INSERT
   
### Skalare Unteraabfrage

- skalare Unterabfrage = Unterabfrage, welche genau einen einzelnen Wert/Spalte/Zeile zurückgibt
- werden mit verschiedenen Operatoren verwendet:
    - =, >, <, >=, <= (nur mit skalarer Abfrage)
      ```
      SELECT name, salary  
      FROM employees  
      WHERE salary > (SELECT AVG(salary) FROM employees);
      ```
    - Hier wollen wir alle Mitarbeiter und ihre Löhne anzeigen, welche einen höheren Lohn als der Durchschnitt der Mitarbeiter haben
        - salary > AVG(salary)


### Nicht-skalare Unterabfrage

- Nicht-skalare Unterabfrage = gibt mehrere Werte oder mehrere Zeilen
- Wird oft mit dem Operator IN, NOT IN, EXISTS, NOT EXISTS, > ALL, = ANY benutzt
- ```
  SELECT name  
  FROM employees  
  WHERE department_id IN (SELECT id FROM departments WHERE location = 'Berlin');
  ```
- hier wird eine Liste mit allen id's zurückgegeben, welche den Standort "Berlin" haben


## Bulkimport

### CSV-Datei vom Server laden

- LOAD DATA INFILE "C:/path/import.csv"
- -> Dateien aus eigenem Dateiesystem lesen

### CSV-Datei vom CLient laden

- LOAD DATA LOCAL INFILE "C:/path/import.csv"
- -> der Klient versucht die Datei aus seinem Dateisystem zu lesen und danach an SQL zu senden

- 

### BSP und Tipps

### Daten aus einer anderen Tabelle einfügen


- ```
  INSET INTO employees (name, email, address)
  SELECT name, email, address FROM old_employees;
  ```


