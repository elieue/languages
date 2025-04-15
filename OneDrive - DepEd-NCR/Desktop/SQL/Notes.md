
# Notes

## Introduction

**SELECT** - used to select columns

' ***** ' - means to select all

**DISTINCT** - used to eliminate duplicates

**FROM** - choose to any table

**WHERE** - find in what column

**IN** - find specific record

**LIKE** - used to find pattern 'A%' means starting with 'A', %z means ending matches with 'z', %the% means anything that containt the word the

**BETWEEN** '_' **AND** ' _' - used to filter certain range

**ORDER BY** - sorts the data in ascending order

**ORDER BY __ DESC** - sorts data in descending order

## Aggregates

* `COUNT()`: returns the number of rows.

  * SELECT COUNT(*)
    FROM table_name;
* `MAX()`: returns the largest value in a column.

  * SELECT MIN(plays)
    FROM playlist;
* `MIN()`: returns the smallest value in a column.
* `SUM()`: returns the total sum in a column.

  * SELECT SUM(plays)
  * FROM playlist;
* `AVG()`: returns the average value in a column.

  * SELECT AVG(plays)
    FROM playlist;

GROUP BY - used to group attributes

---

SQL (Structured Query Language)

- let's us quickly access thru commands

Table names - lowercase

rows - records

columns - fields

Data stored in a servers harddisk

Schema = blueprints of databases

- what tables are included, relationship and what it can hold

Query is the code

Result set yung results

---

Code

SELECT field_name AS alias_name - alias the field to first name

CREATE VIEW field_name AS - showing the results up to date/ saving

to verify ^ SELECT * FROM field_name;

---

## Intermediate SQL

Most common errors:

- Misspelling
- Incorrect capitalization
- Incorrect or missing punctuations, especially commas
