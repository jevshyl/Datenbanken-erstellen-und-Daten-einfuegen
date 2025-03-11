# Theorie Tag 4

## Referenzielle Integrität

- Die referenzielle Intergrität stellt die Konsistenz und Intergrität der Daten sicher
    - z.B. können Datensätze mit einem Fremdschlüssel nur dann gespeichert werden, wenn der Fremdschlüssel tatsächlich existiert.
    - Beziehungen können nur entstehen, wenn es die nötigen Daten wirklich gibt
 - Mit der referenzieller Intergrität werden Anomalien verindert

### Anomalien
- Anomalien = inkonsistente Zustände, zum Beispiel durch redundante Daten oder falsch eingetragene/gelöschte Daten.
- Einfüge-Anomalien:
  - Ein Datensatz soll gespeichert werden, der jedoch keien eindeutigen Primärschlüsselwert hat
      - Einfügen in Tabelle ist nicht möglich
- Änderungs-Anomalien
  - Redundante Informationen Informationen, welche bei einer Änderung nicht beachtet werden
      - Führt zu Verwirrung, man weiss nicht mehr, welche Daten relevant sind und welche nicht
- Lösch-Anomalien
  - Datensätze mit mehreren unabhängigen Informationen füher zu dieser Anomalie
      - Daten sind in einem nicht-normalisierten Zustand
            -Durch Löschen von Daten kann es zu Informationsverlust kommen, da man nicht mehr weiss, welche Daten zu welchen Datensätzen gehören
         

   

## JOINS


- INNER JOIN:
  - kombiniert tabellen -> gibt gemeinsamen Wert (rot) aus
  - Werte die nicht in beiden Tabellen enthalten sind werden nicht angezeigt
  - SELECT * FROM country (tabelle mitFK) INNER JOIN region(tabelle mit PK) ON id_region(FK) region_id(PK);

<img src = "https://github.com/user-attachments/assets/1776f093-43cf-4379-b4e5-0589068b719f" width = "200">

<br> 
<br>

- LEFT OUTER JOIN:
  	- Joined tabellen und gibt den Wert der 1./linken tabelle und des gemeinsamen wertes aus
    	- Also wenn es keine übereinstimmungen hat, dann wird es mit null eingefüllt
  - SELECT * FROM country LEFT OUTER JOIN region ON id_region(FK) = region_id(PK);

<img src = "https://github.com/user-attachments/assets/986be096-1017-46c7-8b11-4c1d833bcbf8" width = "200">

<br> 
<br>

- LEFT EXCLUDING JOIN:
  	- Speziallfall
	- Nur die Einträge der 1./linken tabelle die keine übereinstimmungen haben werden angezeigt
	- SELECT *FROM table_a a 
	LEFT OUTER JOIN table_b b
	ON a.name = b.name
	WHERE b.name IS NULL;

<img src = "https://github.com/user-attachments/assets/73ff298d-0375-4fc5-bc54-176b2b262109" width = "200">

<br> 
<br>

- RIGHT OUTER JOIN
	- Gegenteil von LEFT EXCLUDING JOIN
	- Alle Einträge die keine Übereinstimmungen haben werden angezeigt
	- SELECT *FROM table_a a 
	RIGHT OUTER JOIN table_b b
	ON a.name = b.name
	WHERE a.name IS NULL;
 
<img src = "https://github.com/user-attachments/assets/c8be94ea-a817-4bca-8c78-c5483bd90933" width = "200">

<br> 
<br>

- FULL OUTER JOIN
	- Nimmt ALLE werte der beiden tabellen und deren übereinstimmungen
	- Dort wo es keine übereinstimmungen hat steht null
	- SELECT *FROM table_a a 
	FULL OUTER JOIN table_b b
	ON a.name = b.name;

<img src = "https://github.com/user-attachments/assets/db38ad62-a19e-40c1-9137-a73a19a86a75" width = "200">

<br> 
<br>

- OUTER EXCLUDING JOIN:
	- Zeigt alle werte die nicht übereinstimmen der beiden tabellen
	- Kombi aus right and left excluding join
	- SELECT *FROM table_a a 
	FULL OUTER JOIN table_b b
	ON a.name = b.name
WHERE a.name IS NULL OR b.name IS NULL;
<img src="https://github.com/user-attachments/assets/e7304f9e-d5db-45e1-9e57-47141b8b6593" width = "200">

