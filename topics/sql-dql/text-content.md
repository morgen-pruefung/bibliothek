DQL (Data Query Language) ist ein Teil von SQL und umfasst Befehle, die verwendet werden, um Daten aus einer Datenbank abzurufen. Der wichtigste DQL-Befehl ist SELECT, mit dem Daten abgerufen und gefiltert werden können. DQL konzentriert sich ausschließlich auf das Abrufen und Anzeigen von Daten ohne diese zu verändern.

Wichtige DQL-Befehle:
* SELECT: Abfrage von Daten aus einer oder mehreren Tabellen.
* WHERE: Filtern von Ergebnissen basierend auf einer Bedingung.
* ORDER BY: Sortieren der Ergebnisse.
* DISTINCT: Entfernen von Duplikaten aus den Ergebnissen.
* GROUP BY: Gruppieren von Ergebnissen für Aggregatfunktionen wie COUNT, SUM, AVG.
* LIMIT: Begrenzen der Anzahl der zurückgegebenen Zeilen.

# Einführung in SELECT

Die `SELECT`-Anweisung wird verwendet, um Daten aus einer Datenbank abzurufen.

**Syntax:**
```sql
SELECT spalte1, spalte2, ...
FROM tabelle
WHERE bedingung;
```

---

# Alle Spalten abfragen

Um alle Spalten einer Tabelle anzuzeigen, kannst du `*` verwenden.

**Beispiel:**
```sql
SELECT *
FROM kunden;
```
**Ergebnis:** Zeigt alle Spalten und Datensätze der Tabelle `kunden`.

---

# Bestimmte Spalten abfragen

Du kannst gezielt einzelne Spalten auswählen.

**Beispiel:**
```sql
SELECT vorname, nachname
FROM kunden;
```
**Ergebnis:** Zeigt nur die Spalten `vorname` und `nachname`.

---

# Daten filtern mit WHERE

Mit `WHERE` kannst du die Ergebnisse nach Bedingungen filtern.

**Beispiel:**
```sql
SELECT *
FROM kunden
WHERE land = 'Deutschland';
```
**Ergebnis:** Zeigt alle Kunden, die aus Deutschland kommen.

**Vergleichsoperatoren:**

- `=` (gleich)
- `<>` oder `!=` (ungleich)
- `<, >, <=, >=` (kleiner, größer, usw.)
- `BETWEEN ... AND ...` (Bereichsabfrage)
- `LIKE` (Mustervergleich)
- `IN` (Liste von Werten)

**Beispiel mit LIKE:**
```sql
SELECT vorname
FROM kunden
WHERE vorname LIKE 'A%';
```
**Ergebnis:** Zeigt alle Kunden, deren Vorname mit "A" beginnt.

---

# Sortieren der Ergebnisse mit ORDER BY

Mit `ORDER BY` kannst du die Ergebnisse sortieren.

**Beispiel:**
```sql
SELECT vorname, nachname
FROM kunden
ORDER BY nachname ASC;
```
- **ASC:** Aufsteigend (Standard)
- **DESC:** Absteigend

---

# Doppelte Einträge entfernen mit DISTINCT

`DISTINCT` entfernt Duplikate aus den Ergebnissen.

**Beispiel:**
```sql
SELECT DISTINCT land
FROM kunden;
```
**Ergebnis:** Zeigt jedes Land nur einmal.

---

# Daten aggregieren mit Funktionen

SQL bietet Funktionen wie `COUNT`, `SUM`, `AVG`, `MIN`, und `MAX`.

**Beispiel:**
```sql
SELECT COUNT(*) AS anzahl_kunden
FROM kunden;
```
**Ergebnis:** Gibt die Anzahl aller Kunden zurück.

---

# Gruppierung mit GROUP BY

Mit `GROUP BY` kannst du Ergebnisse gruppieren und Aggregatfunktionen kombinieren.

**Beispiel:**
```sql
SELECT land, COUNT(*) AS anzahl_kunden
FROM kunden
GROUP BY land;
```
**Ergebnis:** Zeigt die Anzahl der Kunden pro Land.

---

# Ergebnisse einschränken mit LIMIT

Mit `LIMIT` kannst du die Anzahl der zurückgegebenen Zeilen begrenzen.

**Beispiel:**
```sql
SELECT *
FROM kunden
LIMIT 5;
```
**Ergebnis:** Zeigt die ersten 5 Datensätze.

---

# Kombinieren von Bedingungen

- **`AND`:** Alle Bedingungen müssen erfüllt sein.
- **`OR`:** Mindestens eine Bedingung muss erfüllt sein.

**Beispiel:**
```sql
SELECT *
FROM kunden
WHERE land = 'Deutschland' AND vorname LIKE 'A%';
```
**Ergebnis:** Zeigt Kunden aus Deutschland, deren Vorname mit "A" beginnt.