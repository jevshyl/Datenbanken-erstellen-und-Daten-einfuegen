# Theorie Tag 2

## Generalisierung und Spezialisierung

- Vorher: Wir haben verschiedene Tabellen, bzw. Entitäten, welche miteinander verknüpft sind. Da wir aber veschiedene Tabellen haben, kann es dazu kommen dass es Attribut gibt, welche diesselben Werte teilen aber auch keine teilen. Dies führt zu Redundanzen, welche man vermeiden möchte. Dies kann man mit der Generalisierung und Spezialisierung machen.



- Generalisierung = gemeinsame Attribute von verschiedenen Entitäten in einem allgemeinen Entitätstyp zusammenfassen
    - man erstellt mehr Tabellen, wobei man aber Redundanzen entfernt
    - man nimmt Attribute und Werte welche in verschiedenen Tabellen sind zusammen in eine neue Tabelle

- Spezialisierung = nicht gemeinsame Attribute bleiben in vorhandenen Entitäten
- Hier werden Untergruppen von den Informationen erstellt, welche zu keinen Redundanzen vorher geführt haben


- Datenverlust vermeiden:
    - Die Datensätze von der spezialisierten Tabellen müssen mit einem Fremdschlüssel auf die generalisierte Tabelle verweisen.
    - Die Beziehung ist die is_a Beziehung
          - "ein Attribut" ist "ein Attribut"



## is_a und has_a Beziehungen

- is_a
    - beschreibt eine Spezialisierung
    - verweist darauf, dass eine Tabelle spezialisiert wurde
    - BSP: Eine Person (Attribut) ist ein Mitarbeiter (anderes Attribut). Die Person bekommt durch die spezialisierte Tabelle (Mitarbeiter) neue Werte.


- has_a:
    - Eine Entität hat eine Beziehung zu einer anderen Entität, bzw. eine Tabelle gehört zu einer anderen Tabelle
    - zeigt keine Generalisierung oder Spezialisierung an
    - zeigt, dass eine Tabelle Werte einer anderen Tabelle besitzt
 

## Identifying Relationship
- Die Identifying Relationship beschreibt die Art der Beziehung zwischen zwei Tabellen
- Man kann genau identifizieiren, was in der eziehung steht
- BSP: Beziehung zwischen Mutter und Kind
- Die Beziehung besteht zwischen zwei Tabellen, eine übergeordnete und eine untergeordnete Tabelle
    - übergeordnete Tabelle: Tabelle mit Primärschlüssel (hier: Mutter)
    - untergeordnete Tabelle: Tabelle ohne Primärschlüssel (hier: Kind)
- Die untergeordnete Tabelle kann ohne eine Beziehung zu der übergeordneten Tabelle nicht exstieren
- Wie: Der Primärschlüssel der übergeordneten Tabelle wird in der untergeordneten Tabelle als Teil des Primärschlüssels gespeichert

## Non-Identifying Relationship
- Diese Bezihungen sind nicht so spezifisch
- Sie beschreibt kurz und knapp, um welche Beziehung es sich handelt
- Bei dieser Beziehung ist die untergeordnete Tabelle nicht von der übergeordneten Tabelle abhängig
- Hier können beide Tabellen auch ohne eine beziehung existieren
- HAS_A - Relationship
- Wie: Fremdschlüssel der überegeordneten Tabelle wird in der untergeordneten Tabelle gespeichert

