In diesem Teil unserer Serie über SQL widmen wir uns komplexeren Abfragen, die es ermöglichen, mächtige Analysen durchzuführen und Daten aus mehreren Tabellen zu kombinieren. Wir werden zwei zentrale Konzepte behandeln: JOINs und Subqueries. Diese Techniken sind unerlässlich für jeden, der mit relationalen Datenbanken arbeitet.

## JOINs in SQL

JOINs ermöglichen es Ihnen, Informationen aus mehreren Tabellen zusammenzuführen. Dies ist besonders nützlich, wenn Ihre Daten über verschiedene Tabellen verteilt sind und Sie eine umfassende Sicht benötigen.

### Arten von JOINs

Es gibt mehrere Arten von JOINs, die für unterschiedliche Anwendungsfälle verwendet werden:

1. **INNER JOIN**: Gibt nur Zeilen zurück, bei denen es in beiden Tabellen Übereinstimmungen gibt.
2. **LEFT (OUTER) JOIN**: Gibt alle Zeilen aus der linken Tabelle und die übereinstimmenden Zeilen aus der rechten Tabelle zurück; Nichtübereinstimmungen werden mit NULL gefüllt.
3. **RIGHT (OUTER) JOIN**: Ähnlich wie LEFT JOIN, aber für die rechte Tabelle.
4. **FULL (OUTER) JOIN**: Gibt alle Zeilen von beiden Tabellen zurück und fügt NULLs hinzu, wo keine Übereinstimmung besteht.

### Beispiel mit INNER JOIN

Angenommen, Sie haben zwei Tabellen: `Kunden` und `Bestellungen`. Jede Bestellung in der Tabelle `Bestellungen` ist einem Kunden zugeordnet durch eine `KundenID`.

- **Tabelle `Kunden`:**
  - `ID`
  - `Name`

- **Tabelle `Bestellungen`:**
  - `BestellNr`
  - `Datum`
  - `KundenID`

Um alle Bestellungen zusammen mit den Namen der Kunden zu sehen, verwenden Sie:

```sql
SELECT Kunden.Name, Bestellungen.BestellNr, Bestellungen.Datum
FROM Kunden
INNER JOIN Bestellungen ON Kunden.ID = Bestellungen.KundenID;
```

Dieses Beispiel zeigt nur die Bestellungen an, für die ein Kunde existiert.

## Subqueries

Subqueries sind eingebettete Abfragen innerhalb einer größeren SQL-Anweisung. Sie bieten eine flexible Möglichkeit, komplexe Datenabfragen zu formulieren und werden oft in Verbindung mit JOINs verwendet.

### Subquery als WHERE-Klausel

Eine häufige Anwendung ist die Nutzung von Subqueries zur Einschränkung der Ergebnisse. Zum Beispiel, um Kunden zu finden, die Bestellungen im Jahr 2023 gemacht haben:

```sql
SELECT Name FROM Kunden
WHERE ID IN (SELECT KundenID FROM Bestellungen WHERE YEAR(Datum) = 2023);
```

Diese Abfrage sucht nach allen KundenIDs in `Bestellungen`, bei denen das Datum auf das Jahr 2023 fällt, und verwendet diese IDs dann, um die entsprechenden Namen aus der Tabelle `Kunden` abzurufen.

### Subquery als Teil eines SELECT

Subqueries können auch direkt im SELECT-Teil einer Abfrage auftauchen. Angenommen, Sie möchten für jeden Kunden die Anzahl seiner Bestellungen sehen:

```sql
SELECT Name,
       (SELECT COUNT(*) FROM Bestellungen WHERE KundenID = Kunden.ID) AS AnzahlBestellungen
FROM Kunden;
```

Diese Subquery zählt alle Bestellungen für jeden einzelnen Kunden.

## Fazit

JOINs und Subqueries sind mächtige Werkzeuge in SQL. JOINs ermöglichen die Kombination von Daten aus mehreren Tabellen, während Subqueries zusätzliche Flexibilität bieten, komplexe Abfragen zu erstellen. Diese Techniken erweitern Ihre Möglichkeiten zur Datenauswertung und -analyse erheblich.

In den kommenden Artikeln werden wir tiefer in die Themen Datenmanipulation mit UPDATE- und DELETE-Anweisungen eintauchen sowie Sicherheitsaspekte von SQL behandeln. Bleiben Sie dran, um Ihr Wissen weiter zu vertiefen!