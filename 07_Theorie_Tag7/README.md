# Theorie Tag 7

## Datensicherung von Datenbanken

- Als Beispiel kann man sich vorstellen, dass man eine Website hostet, welche auf eine Datenbank zugreifen kann. Diese Website kann mmit der Datenbank interagieren wobei ein gegenseitiger Datenaustausch stattfindet.
  - Nutzer können zum Beispiel Daten in der Datenbank speichern
  - Nutzer können Daten aus einer Datenbank auslesen
- Dadurch, dass man als Nutzer eigene daten in die Datenbank eintragen kann, passiert es oft, dass diese Datenbanken sensible Kundendaten, persöhnliche Informationen oder sogar Personal- und Finanzinformationen enthalten
- Wenn die Website jetzt aber Ausfällt, falsche Daten werden angezeigt oder die Website ladet gar nicht mehr.  - Dies kann für Vertrauernsverlust beim Kunden sorgen
 - Für die verantwortliche Person führt das zu mehr Arbeit, diese Fehler zu beheben
- Somit kann man sagen, dass ein Datenverlust stattfindet
  - Ursachen dafür sind technische Versage der Hardware oder auch einfach Benutzerfehler
    - Kann auch ein Angriff von aussen sein
- Lösung, damit Datenverlust nicht nicht rückkehrbar ist: **Datensicherung**

## Sicherung von Datenbanken 

- Das allgemeine Prinzip besagt, dass man, um einen Datenverlust zu verhinden, Sicherheitskopien der Datenbanken auf externen Speicermedien erstellen soll. Diese Kopien werden als Backups bezeichnet und können einen bestimmten Zustand der Datenbank wiederherstellen
### Offline- und Online-Backups
- Es gibt sogenannte Offline- und Online-Backups
- Online Backups:
  - Backup wird erstellt, ohne dass man die Datenbank herunterfahren muss
  - Wie passiert das mit dem Datenaustausch:
    - Während dieses Backups kann der Datenaustausch immernoch stattfinden
    - Während des Sicherzungsprozesse nimmt die Datenbank die Änderungen die während dem Backup passiert sind und speichert diese in einem seperaten Bereich. Erst wenn das Backup erstellt wurde, werden diese Daten an die Sicherung angefügt
- Offline Backups:
  - Man fährt die Datenbank komplett herunter und erstellt dann ein Backup davon
    - Keine Datenaustausch findet während dieser Zeit statt
    - bzw. alle Anwendungen, welche die datenbank benötigen können während dieser Zeit nicht benutzt werden
   
### Zusätziche Backups

- Neben Online- und Offine-Backups gibt es zusätzliche Möglichkeiten für die Datensicherung
<br>
- **Vollbackup**
  - Ein Vollbackup = Backup von allen Daten
  - Vorteile:
    - Alle Daten werden gespeichert, kleine Chance des Datenverlusts
  - Nachteil:
    - Benötigt sehr viel Speicherplatz
  - Widerherstellung:
    - Für das Widerherstellen von Daten braucht man nur das letzte Vollbackup
  - Wie oft würde man diese erstellen müssen_
    - Einmal pro Woche 

- **Differentielles Backup**
  1. Hier wird zuerst ein Voll-Backup der Datenbank erstellt.
  2. Dann schaut sich die Sicherung an, welche Daten seit dem letzten Backup verändert wurden
  3. Nur die Daten, welche sich verändert haben oder neu dazugekommen sind, werden gesichert
  - Vorteile:
    - Nimmt vielweniger Speicherplatz ein
  - Nachteile:
    - geänderte oder neue Daten werden bis zum nächsten Vollbackup bei jedem differentiellem Backup erneut kopiert.
  - Widerherstellung:
    - Widerherstellung von Daten benötigt das letzet Vollbackup und alle gewünschten differentielle Backups
      - kann zu Fehlern führen -> mehr Arbeit im Falle der Fehler
  - Wie oft:
    - tägliches Backup
    - wöchentlich mit Vollbackup vergelichen/anpassen/einfügen

- **Inkrementelles Backup**
  - Zusätzlich zu einem Voll-Backup werden beim inkrementellem Backup nur die Daten kopiert, welche sich seit dem letztem Mal verändert haben.
  - Unterschied zu differenteillem Backup:
      - Das inkrementelle Backup bezieht sich immer auf das vorherige Voll-Backup und inkrementelle Backup
      - Als werden nicht alle Änderungen seit dem letzten Voll-Backup als neue Kopien immer wieder gespeichert, sondern nur das wird neu gespeichrt, was sich seit dem letzten inkrementellen + Voll-Backup verändert hat
  - Vorteile:
    - Man braucht noch weniger Speicherplatz, da jede Datei nur einmal gespeichert wird
  - Widerherstellung:
    - alle Sicherungen vom Voll-Backup bis zu einem gewissen Stand werden benötigt
- Wie oft:
  - täglich -> immer mehr Daten werden jeden Tag gespeichert
  - wöchentlich mit Voll-Backup anpassen/abgleichen/erstellen
 

## 
