# Grundlagen SQL

In diesen Thema werde ich dir die grundlegenden SQL Befehle näher erläutern.

## Daten abfragen (SELECT)

Syntax: `SELECT spalten FROM tabelle WHERE bedinung;`

Wichtige Schlüsselwörter:
- `SELECT`: es folgen die Spalten, die du angezeigt haben willst. (Verwende `*`, um alle anzuzueigen)
- `FROM`: es folgen die Tabellen, von denen die Daten stammen
- `WHERE`: es folgen Bedinungen, welche die Daten eingrenzen. Falles es keine Bedinungen geben soll, kann man das WHERE weglassen

Beispiel Aufgaben:

1: Zeige alle Kunden an.
```sql
SELECT * FROM Kunden;
```

2: Zeige den Name und das Geburtsdatum aller Kunden an, die in Deutschland wohnen.
```sql
SELET Name, Geburtsdatum
FROM Kunden
WHERE Land = 'Deutschland';
```
Tipp: es empfiehlt sich immer Schlüsselwörter, wie SELECT, FROM und WHERE untereinander zu schreiben in der Klausur. Dies ist übersichtlicher und du hast mehr Platz Fehler zu korrigieren, wenn dir welche auffallen während der Klausur.

3: Zeige den Name und das Geburtsdatum aller Kunden an, die in Deutschland oder Österreich wohnen.
```sql
SELET Name, Geburtsdatum
FROM Kunden
WHERE Land = 'Deutschland'
  OR Land = 'Österreich';
```
Tipp: du kannst Bedinungen auch mit `AND` verknüpfen.

4: Zeige alle Mitarbeiter an, die in der Produktion arbeiten und sortiere sie absteigend nach dem Gehalt.
```sql
SELECT *
FROM Mitarbeiter
WHERE Abteilung = 'Produktion'
ORDER BY Gehalt DESC;
```
Mit `ORDER BY` kannst du nach bestimmte Spalten sortieren. `DESC` bedeutet descending (absteigend) und `ASC` bedeutet ascending (aufstigend)


5: Zeige den Mitarbeiter an, der am meisten Geld verdient und im Einkauf arbeitet.
```sql
SELECT *
FROM Mitarbeiter
WHERE Abteilung = 'Einkauf'
ORDER BY Gehalt DESC
LIMIT 1;
```
Das Schlüsselwort `LIMIT` begrenzt die Anzahl der Reihen auf den angegeben Wert.