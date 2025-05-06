# Theorie Tag 10

## Common Table Expressions CTEs

- CTE = Common Table Expressions
- CTE ist das Konzept, Abfragen zu vereinfachen und die Lesbarkeit von SQL-Statements zu erhöhen
- Also ist das CTE eigentich eine temporäre Ergebnismenge, die in einer SELECT, INSERT, UPDATE oder DELETE Abfrage definiert wird
  - Da es eine temporäres Ergbnismenge ist, verändert diese Art von Abfrage nicht an der Datenbank
  - Diese Art von Abfrage dient für komplexe Abfragen und um diese vereinfachter zu erstellen
 
### Wie wird diese Art von Abfrage erstellt?

```
WITH MitarbeiterAbteilung AS (
  SELECT name, abteilung
  FROM Mitarbeiter
  WhERE Abteilun = 'IT'
)

SELECT Name FROM MitarbeiterAbteilung;
```


## Stored Procedures

- Stored Procedures = vordefineirte SQL-Abfolgen
- Man verwedet diese Art von Abfragen um gewissen SQL-Code wiederholt verwenden zu können
- Sie verbessern auch die Performance und könnnen für komplexe Abfragen genutzt werden, um diese vereinfacht zu erstellen
<br>
- Stored procedures sind eigentlich Samllungen von SQL-Befehlen, welche in der Datenbank gespeichert werde

### Merkmale

- Wiederverwendbarkeit
- Zentralisierung der Logik
- Verbesserte Performance
- Sicherheit

### Wie wird eine solche Abfrage erstellt?


```
DELIMITER $$

CREATE PROCEDURE GetKundenDaten (IN kunden_id INT)
BEGIN
    SELECT name, adresse, telefon
    FROM kunden
    WHERE id = kunden_id;
END $$

DELIMITER ;

```

- GetKundenDaten = Stored Procedure wird mit diesem Namen erstellt
- kunden_id = Parameter, welcher eingegeben werden muss, um diese Daten zu bekommen
- DELIMITER = Anweisung, um Trennzeichen von zuerst ; zu $$ und dann zurück zu ; zu verändern


```
CALL GetKundendaten(1);
```

- Mit dieser Abfrage kann man nun diese vordefineirte Abfrage abrufen
- Der Wert 1 in der Klammer defineirt, nach welcher kunden_id man sucht
