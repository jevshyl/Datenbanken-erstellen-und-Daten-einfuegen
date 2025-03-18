# Theorie Tag 5

## Löschen von Daten in professionellen Datenbank

- Üblicherweise ist der Lösch-Befehl "delete" in professionellen Datenbanken nicht erlaubt
    - Wieso? Dieser Befehl würde zu starkem Datenverlust führen
- Was passiert beim ausführen dieses Befehls:
    - Wenn ich zum Beispiel einen Mitarbeiter aus einer Tabelle löschen will und den Befehl "delete" dafür verwede, dann verschwindet nicht nur der Datensatz des Mitarbeiters, sondern auch alle Beziehungen, welche mit dem Mitarbeiter in Verbindung standen
        - Wenn das passiert, dann kann man von der Datenbank aus nicht mehr verstehen, welche Position und Beziehungen dieser Mitarbeiter zuvor hatte. Welchen Job er hatte, ob er eine Führungsposition oder -bezihung hatte und viel mehr.
            - Bzw. viele Aktivitäten wären nicht mehr nachvollziehbar -> kann auch zu juristischen Problemen führen
- Was kann man tun:
    - Als Lösung kann man z.B. den Datensatz nciht löschen, sondern umgekehrt erweiter und zum Beispiel als inaktiv markieren
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
          


