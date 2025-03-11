# Theorie Tag 4

## Referenzielle Integrität

- Die referenzielle Intergrität stellt die Konsistenz und Intergrität der Daten sicher
    - z.B. können Datensätze mit einem Fremdschlüssel nur dann gespeichert werden, wenn der Fremdschlüssel tatsächlich existiert.
    - Beziehungen können nur entstehen, wenn es die nötigen Daten wirklich gibt
 - Mit der referenzieller Intergrität werden Anomalien verindert
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
            - Durch Löschen von Daten kann es zu Informationsverlust kommen, da man nicht mehr weiss, welche Daten zu welchen Datensätzen gehören
         

   

## JOINS
