# Repetition 

## Datenmodellierung Theorie

1. Konzeptionelles Datenmodell (ERM)
    - Entity Relationship Model
    - Model, welches für das fachliche Verständnis abgebildet wird
    - Skizze
2. Logisches Datenmodell (ERD)
    - Entity Relationship Diagram
    - die Abbildung des ERM's
    - genauere und detaillierte Abbildung, welche später in die Datenbank mit derselben Struktur      implementiert wird
3. Physisches Datenmodell
    - die Datenbank, die Tabelle oder das Schrma werden erstellt
    - Commands wire CREATE TABLE usw werden heir genutzt
    - Die Datenbak wird erstellt


 ## Normalisiserung

1. Normalisierung:
   - " Die erste Normalform (1NF) ist dann erfüllt, wenn die Wertebereiche der Attribute des Relationstypen atomar vorliegen "
   - atomar = einzeln
   - jede Zeile darf nur einen Wert enthalten
   - erst wenn alle Attribute getrennt vorliegen is die 1NF erfüllt

2. Normalisierung
   - "Ein Relationstyp (Tabelle) befindet sich genau dann in der zweiten Normalform (2NF), wenn er sich in der ersten Normalform (1NF) befindet und jedes Nichtschlüsselattribut von jedem Schlüsselkandidaten voll funktional abhängig ist."
   - Man trennt die "grosse" Tabelle die man zuvor bekommen hat in weutere kleinere Tabellen
   - Man bildet Gruppen, bzw man trennt Objekt-Typen voneinander.
   - Zusätzlich definiert man Primär- und Fremdschlüssel.
         - Primärschlüssel: ID der Spalte
         - Fremdschlüssel: referenziert eine andere Tabelle durch dessen Prümärschlüssel
   - Beziehungen/Kardinalitäten erstellen:
       - [Link zu Kardinalitäten](#Kardinalitäten)
   - Die 2NF wird dann erfüllt, wenn man keine doppelten Werte und aufgeteilte Tabellen mit Beziehungen zuenandedr hat.


3. Normalisierung:
   - "Ein Relationstyp befindet sich genau dann in der dritten Normalform (3NF), wenn er sich in der zweiten Normalform (2NF) befindet und kein Nichtschlüsselattribut transitiv von einem Kandidatenschlüssel abhängt."
   - in der 3NF darf jedes Attribut nur noch von einem Primärschlüssel abhängig sein
   - Die Tabellen können weiter gespaltet werden, neue Beziehungen entstehen
   


## Kardinalitäten

- 1:1 (Eins zu Eins)
  - Ein Datensatz in Tabelle 1 kann maximal einem Datensatz in Tabelle 2 zugeprdnet sein
  - z.B ein Mensch kann nur maxima eine ID haben
- 1:N (Eins zu Vielen)
    - Ein Datensatz in Tabelle 1 kann mit mehreren Datensätzen in Tabelle 2 verbunden sein, jedoch können die Datensätze in der Tabelle 2 nur mit maximal einem Datensatz in Tabelle 1 verbunden sein
    - z.B Ein Klassenlehrer unterrichtet mehrere Schüler aber jeder Schüler hat nur einen Klassenlehrer.
- M:N (Viele zu Viele)
    - Ein Datensatz in Tabelle 1 kann mit mehreren Datensätzen in Tabelle 2 verbunden sein und umgekehrt.
    - Ein Schüler kann mehrere Kurse besuchen und jeder Kurs hat mehrere Schüler

