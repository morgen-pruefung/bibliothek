Willkommen zu unserer Serie über SQL – die Sprache, die das Rückgrat der meisten modernen Datenbankanwendungen bildet. In diesem Artikel befassen wir uns mit den Grundlagen von SQL und lernen, wie man einfache Abfragen erstellt, um Daten aus einer Datenbank abzurufen. Ob Sie neu in der Welt der Datenbanken sind oder lediglich Ihr Wissen auffrischen möchten, dieser Einstieg bietet Ihnen eine solide Basis.

## Was ist SQL?

SQL steht für Structured Query Language und wird verwendet, um mit relationalen Datenbankmanagementsystemen (RDBMS) zu kommunizieren. Es ermöglicht Ihnen, Daten abzufragen, einzufügen, zu aktualisieren oder zu löschen – kurz gesagt: jegliche Form von Interaktion mit den in einer Datenbank gespeicherten Informationen.

## Grundlegende SELECT-Abfrage

Die am häufigsten verwendete SQL-Anweisung ist `SELECT`, die es Ihnen erlaubt, Daten aus einer oder mehreren Tabellen abzurufen. Beginnen wir mit einem einfachen Beispiel:

### Beispiel-Datenbank: Kundenverzeichnis

Stellen Sie sich vor, Sie haben eine Tabelle namens `Kunden` mit folgenden Spalten:

- `ID`: Ein eindeutiger Kennungswert für jeden Kunden.
- `Name`: Der Vorname und Nachname des Kunden.
- `Email`: Die E-Mail-Adresse des Kunden.
- `Alter`: Das Alter des Kunden in Jahren.

### Erste SELECT-Abfrage

Um alle Daten aus der Tabelle `Kunden` abzurufen, verwenden Sie die folgende Abfrage:

```sql
SELECT * FROM Kunden;
```

Die Sternchen (*) sind ein Platzhalter für "alle Spalten", was bedeutet, dass diese Anweisung alle Zeilen und alle Spalten aus der `Kunden`-Tabelle zurückgibt.

### Spezifische Daten abrufen

Nicht immer benötigen Sie alle Informationen. Angenommen, Sie möchten nur die Namen und E-Mail-Adressen aller Kunden sehen:

```sql
SELECT Name, Email FROM Kunden;
```

Dies gibt Ihnen eine Liste mit den spezifizierten Spalten, wodurch unnötige Daten ausgeblendet werden.

### Abfrage unter Verwendung von Bedingungen

Um Ihre Ergebnisse weiter einzuschränken, können Sie die `WHERE`-Klausel verwenden. Zum Beispiel, um nur Kunden älter als 30 zu finden:

```sql
SELECT Name, Alter FROM Kunden WHERE Alter > 30;
```

### Sortieren der Ergebnisse

Die Reihenfolge Ihrer Daten kann durch die `ORDER BY`-Klausel geändert werden. Um die resultierende Liste der über 30-Jährigen alphabetisch zu sortieren:

```sql
SELECT Name, Alter FROM Kunden WHERE Alter > 30 ORDER BY Name;
```

### LIMIT verwenden

In einigen Situationen möchten Sie nur eine bestimmte Anzahl von Ergebnissen sehen. Mit `LIMIT` können Sie die Anzahl der zurückgegebenen Zeilen begrenzen. Zum Beispiel die ersten fünf Kunden:

```sql
SELECT * FROM Kunden LIMIT 5;
```

## Fazit

Sie haben nun einen Einblick in die Grundlagen von SQL erhalten. Diese einfachen Abfragen sind nur der erste Schritt auf Ihrem Weg zum Verständnis dieser leistungsfähigen Datenbankabfragesprache. In den folgenden Artikeln unserer Serie werden wir komplexere Themen wie JOINs, Subqueries und Datenmanipulation erörtern.

Praktizieren Sie die hier vorgestellten Abfragen anhand einer lokalen oder Online-Datenbankumgebung, um ein besseres Verständnis zu entwickeln. Mit diesen grundlegenden Kenntnissen sind Sie nun gut gerüstet, um weiter in die Welt von SQL einzutauchen.