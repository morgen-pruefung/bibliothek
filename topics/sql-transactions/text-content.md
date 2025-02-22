In relationalen Datenbankmanagementsystemen ist die Aufrechterhaltung der Datenintegrität von höchster Bedeutung. Eine zentrale Rolle spielen dabei Transaktionen, die als grundlegende Arbeitsblöcke fungieren, um sicherzustellen, dass alle vorgenommenen Änderungen in einer Einheit abgeschlossen werden oder gar nicht. In diesem Artikel beleuchten wir das Konzept der Transaktionen und deren Verwaltung mittels `COMMIT`, `ROLLBACK` und `SAVEPOINT`.

## Was sind Transaktionen?

Eine Transaktion ist eine Folge von Datenbankoperationen, die als atomare Einheit behandelt werden müssen. Das bedeutet, dass alle Operationen innerhalb einer Transaktion entweder vollständig durchgeführt oder gar nicht ausgeführt werden. Die Eigenschaften der Transaktionsintegrität, bekannt unter dem Akronym ACID (Atomicity, Consistency, Isolation, Durability), sorgen für die Zuverlässigkeit und Konsistenz von Datenbankoperationen.

### Eigenschaften von Transaktionen

1. **Atomarität**: Eine Transaktion ist entweder vollständig abgeschlossen oder wird gar nicht ausgeführt.
2. **Konsistenz**: Nach einer erfolgreichen Transaktion bleibt die Datenbank in einem konsistenten Zustand.
3. **Isolation**: Die Ausführung paralleler Transaktionen führt zu keinem inkonsistenten Zustand der Datenbank.
4. **Dauerhaftigkeit**: Nach Abschluss wird die durch eine Transaktion erzielte Änderung dauerhaft in der Datenbank gespeichert.

## Verwaltung von Transaktionen

Um Transaktionen in SQL effektiv zu handhaben, werden drei Hauptbefehle verwendet: `COMMIT`, `ROLLBACK` und `SAVEPOINT`.

### COMMIT

Der `COMMIT`-Befehl wird verwendet, um eine Transaktion abzuschließen. Alle Änderungen, die während der Transaktion gemacht wurden, werden in diesem Moment permanent in der Datenbank gespeichert.

#### Beispiel:

```sql
BEGIN TRANSACTION;

UPDATE Konten SET Saldo = Saldo - 100 WHERE KontoID = 1;
UPDATE Konten SET Saldo = Saldo + 100 WHERE KontoID = 2;

COMMIT;
```

In diesem Fall werden beide Aktualisierungen beibehalten, da der `COMMIT`-Befehl ausgeführt wurde.

### ROLLBACK

Der `ROLLBACK`-Befehl dient dazu, alle Änderungen einer Transaktion rückgängig zu machen. Er wird verwendet, wenn ein Fehler auftritt oder eine Bedingung nicht erfüllt ist und die Auswirkungen der Transaktion verhindert werden müssen.

#### Beispiel:

```sql
BEGIN TRANSACTION;

UPDATE Konten SET Saldo = Saldo - 100 WHERE KontoID = 1;
-- Angenommen, ein Fehler tritt hier auf oder eine Bedingung wird nicht erfüllt
ROLLBACK;
```

Durch den `ROLLBACK`-Befehl wird das System in den Zustand zurückversetzt, der vor Beginn der Transaktion existierte.

### SAVEPOINT

Mit einem `SAVEPOINT` können innerhalb einer Transaktion Zwischenstände gespeichert werden. Dies ermöglicht es, eine Transaktion bis zu einem bestimmten Punkt rückgängig zu machen, ohne den gesamten Prozess abbrechen zu müssen.

#### Beispiel:

```sql
BEGIN TRANSACTION;

UPDATE Konten SET Saldo = Saldo - 100 WHERE KontoID = 1;
SAVEPOINT vorZweiterUpdate;
UPDATE Konten SET Saldo = Saldo + 50 WHERE KontoID = 2;

-- Wenn ein Fehler auftritt oder eine Bedingung nicht erfüllt ist
ROLLBACK TO SAVEPOINT vorZweiterUpdate;

COMMIT;
```

In diesem Beispiel werden die Änderungen nach dem zweiten Update rückgängig gemacht, während die erste Aktualisierung bestehen bleibt.

## Fazit

Transaktionen spielen eine wesentliche Rolle bei der Gewährleistung von Datenintegrität und -konsistenz in einer Datenbank. Durch den strategischen Einsatz von `COMMIT`, `ROLLBACK` und `SAVEPOINT` können Entwickler sicherstellen, dass ihre Anwendungen zuverlässig mit Transaktionen umgehen. Diese Werkzeuge bieten die Flexibilität, Fehler zu handhaben und Änderungen kontrolliert zu verwalten, was letztlich zur Stabilität und Zuverlässigkeit von Datenbankanwendungen beiträgt.

In den kommenden Artikeln werden wir uns tiefergehend mit weiteren fortgeschrittenen Themen im Bereich der Datenbankadministration befassen. Bleiben Sie dran!