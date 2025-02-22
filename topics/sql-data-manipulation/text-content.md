In diesem Artikel befassen wir uns mit der Manipulation von Daten in relationalen Datenbanken mittels SQL (Structured Query Language). Die Data Manipulation Language (DML) umfasst drei wesentliche Operationen: `INSERT`, `UPDATE` und `DELETE`. Diese Anweisungen ermöglichen es, neue Datensätze einzufügen, bestehende zu aktualisieren oder unerwünschte Daten aus einer Tabelle zu entfernen. Lassen Sie uns einen genaueren Blick auf diese wichtigen Funktionen werfen.

## INSERT: Neue Daten einfügen

Mit der `INSERT`-Anweisung können neue Datensätze in eine Tabelle eingefügt werden. Dies ist essentiell, um Datenbanken mit neuen Informationen zu versorgen und aktuell zu halten.

### Syntax

Die Grundstruktur einer `INSERT`-Anweisung lautet:

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

#### Beispiel

Angenommen, Sie haben eine Tabelle namens `Kunden`, mit den Spalten `ID`, `Name` und `Email`. Um einen neuen Kunden hinzuzufügen, könnten Sie folgendes tun:

```sql
INSERT INTO Kunden (ID, Name, Email)
VALUES (1, 'Max Mustermann', 'max.mustermann@example.com');
```

### INSERT mit SELECT

Sie können auch Daten aus einer anderen Tabelle oder Abfragequelle einfügen:

```sql
INSERT INTO TabelleZiel (Spalte1, Spalte2)
SELECT SpalteA, SpalteB
FROM Quelltabelle
WHERE Bedingung;
```

## UPDATE: Bestehende Daten aktualisieren

Mit der `UPDATE`-Anweisung können bestehende Datensätze in einer Tabelle bearbeitet werden. Dies ist nützlich, um Informationen zu korrigieren oder zu erweitern.

### Syntax

Die allgemeine Form der `UPDATE`-Anweisung sieht so aus:

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

#### Beispiel

Wenn Sie den E-Mail-Adressen des Kunden Max Mustermann aktualisieren möchten, verwenden Sie:

```sql
UPDATE Kunden
SET Email = 'neuer.email@example.com'
WHERE Name = 'Max Mustermann';
```

Achten Sie darauf, die `WHERE`-Klausel sorgfältig zu formulieren, um nur die gewünschten Zeilen zu aktualisieren.

## DELETE: Daten entfernen

Die `DELETE`-Anweisung wird verwendet, um unerwünschte oder veraltete Datensätze aus einer Tabelle zu löschen. Dies hilft dabei, Datenbanken schlank und aktuell zu halten.

### Syntax

Ein typisches `DELETE`-Statement sieht so aus:

```sql
DELETE FROM table_name
WHERE condition;
```

#### Beispiel

Um den Kunden Max Mustermann komplett aus der Tabelle zu entfernen, würden Sie schreiben:

```sql
DELETE FROM Kunden
WHERE Name = 'Max Mustermann';
```

### Wichtigkeit der WHERE-Klausel

Beachten Sie, dass beim Ausführen einer `DELETE`-Anweisung ohne eine `WHERE`-Klausel alle Datensätze in der Tabelle gelöscht werden. Daher sollte immer eine Bedingung angegeben werden.

## Fazit

Die Datenmanipulation mit SQL über die Anweisungen `INSERT`, `UPDATE` und `DELETES` ist entscheidend für die Verwaltung von Inhalten innerhalb einer relationalen Datenbank. Mit diesen Werkzeugen können Sie sicherstellen, dass Ihre Datenbank aktuell, präzise und organisiert bleibt.

In den nächsten Artikeln werden wir uns mit fortgeschritteneren Themen wie Transaktionen und Sicherheitsaspekten bei der Datenmanipulation befassen. Bleiben Sie dran!