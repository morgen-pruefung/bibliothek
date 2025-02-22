Datenbankdesign ist eine komplexe Aufgabe, die viele Aspekte umfasst, darunter Leistungsoptimierung, Integritätssicherung und Skalierbarkeit. Eine wichtige Methode zur Erreichung dieser Ziele ist die Datenbanknormalisierung. Normalisierung bezieht sich auf den Prozess der Organisation einer Datenbank in eine Form, die Redundanz minimiert und die Konsistenz von Daten gewährleistet. Dieser Artikel wird die ersten drei Normalformen (1NF, 2NF, 3NF) erläutern und mit praktischen Beispielen illustrieren.

## Was ist Normalisierung?

Normalisierung ist eine Methode zur Strukturierung einer Datenbank so, dass Redundanz von Daten vermieden wird und die Integrität der gespeicherten Informationen sichergestellt ist. Der Prozess umfasst mehrere Stufen oder "Normalformen", beginnend mit der ersten Normalform (1NF) bis hin zu höheren Stufen wie 2NF, 3NF usw.

### Zweck der Normalisierung

- **Reduzierung von Redundanz**: Vermeidung unnötiger Duplikation von Daten.
- **Verbesserung der Integrität**: Sicherstellung konsistenter und genauer Daten.
- **Einfachere Wartung**: Erleichterung von Aktualisierungen, Einfügungen und Löschungen.

## Die ersten drei Normalformen

### 1. Erste Normalform (1NF)

Eine Tabelle ist in der ersten Normalform, wenn sie die folgenden Kriterien erfüllt:

- **Jeder Spalte gibt es eindeutige Werte**: Keine wiederholten Gruppen oder Listen.
- **Primärschlüssel**: Jede Zeile hat einen Primärschlüssel, der die Einzigartigkeit jeder Datensatz gewährleistet.

#### Beispiel

**Unnormalisierte Tabelle:**

| StudentID | Name  | Kurse                    |
|-----------|-------|--------------------------|
| 1         | Alice | Mathematik, Physik       |
| 2         | Bob   | Chemie, Biologie         |

In der obigen Tabelle enthält die Spalte "Kurse" wiederholte Gruppen von Daten. Um in die 1NF zu gelangen:

**Normalisierte Tabelle:**

| StudentID | Name  | Kurs       |
|-----------|-------|------------|
| 1         | Alice | Mathematik |
| 1         | Alice | Physik     |
| 2         | Bob   | Chemie     |
| 2         | Bob   | Biologie   |

### 2. Zweite Normalform (2NF)

Eine Tabelle ist in der zweiten Normalform, wenn sie:

- In der ersten Normalform ist.
- Jede nicht-schlüsselbezogene Spalte vollständig von der Gesamtheit des Primärschlüssels abhängt.

#### Beispiel

**Unnormalisierte Tabelle (noch nicht in 2NF):**

| StudentID | Kurs       | DozentName    |
|-----------|------------|---------------|
| 1         | Mathematik | Dr. Smith     |
| 1         | Physik     | Dr. Johnson   |
| 2         | Chemie     | Dr. Lee       |
| 2         | Biologie   | Dr. Brown     |

In dieser Tabelle ist "DozentName" nicht vollständig von der Kombination aus "StudentID" und "Kurs" abhängig; es hängt nur vom "Kurs". Um in die 2NF zu gelangen, trennen wir die Daten:

**Normalisierte Tabellen (in 2NF):**

**Tabelle: StudentCourses**
| StudentID | Kurs       |
|-----------|------------|
| 1         | Mathematik |
| 1         | Physik     |
| 2         | Chemie     |
| 2         | Biologie   |

**Tabelle: CourseInstructors**
| Kurs       | DozentName    |
|------------|---------------|
| Mathematik | Dr. Smith     |
| Physik     | Dr. Johnson   |
| Chemie     | Dr. Lee       |
| Biologie   | Dr. Brown     |

### 3. Dritte Normalform (3NF)

Eine Tabelle ist in der dritten Normalform, wenn sie:

- In der zweiten Normalform ist.
- Keine transitiven Abhängigkeiten zwischen nicht-schlüsselbezogenen Attributen enthält.

#### Beispiel

**Unnormalisierte Tabelle (noch nicht in 3NF):**

| DozentID | DozentName | Fach          |
|----------|------------|---------------|
| 101      | Dr. Smith  | Mathematik    |
| 102      | Dr. Johnson| Physik        |

In dieser Tabelle ist "Fach" abhängig von "DozentName", nicht direkt vom Primärschlüssel "DozentID". Um in die 3NF zu gelangen:

**Normalisierte Tabellen (in 3NF):**

**Tabelle: Instructors**
| DozentID | DozentName |
|----------|------------|
| 101      | Dr. Smith  |
| 102      | Dr. Johnson|

**Tabelle: InstructorCourses**
| DozentID | Fach          |
|----------|---------------|
| 101      | Mathematik    |
| 102      | Physik        |

## Fazit

Die Normalisierung ist ein grundlegender Schritt im Datenbankdesign, der dazu beiträgt, Redundanz zu minimieren und die Integrität von Daten zu gewährleisten. Durch die Anwendung der ersten drei Normalformen können wir eine strukturierte und effiziente Datenbank erstellen. Dies ermöglicht nicht nur eine bessere Leistung, sondern auch einfachere Wartung und Erweiterbarkeit.