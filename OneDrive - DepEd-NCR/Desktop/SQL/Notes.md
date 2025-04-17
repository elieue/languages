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
* ROUND(): 

GROUP BY - used to group attributes

### Arithmetic

+, -, *, and /

note: always used alias

Example

SELECT (4+3);

SELECT title, duration, duration / 60.0 AS duration_hours
FROM films;

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

---

## Filtering Records

<> = not equal to

OR = satisfy at least one condition (need to specify field name)

AND = both situation must be satisfy (need to specify field name)

note: can have multiple and

BETWEEN __ AND __- filtering values within specific range

#### Example:

SELECT title, release_year
FROM films
WHERE (release_year BETWEEN 1994 AND 2000)
AND (language = 'English' OR language = 'Spanish')
AND gross > 2000000;

SELECT ROUND(AVG(facebook_likes),1) AS avg_facebook_likes

FROM reviews;

### Filtering Text

- Filter a pattern rather than specific text
- LIKE

  - used to search for a pattern in a field
  - % match zero, one, or many characters
    - SELECT name
    - FROM people
    - WHERE name LIKE 'Ade%';
      - Starts with Ade
      - '%ade' end with ade
  - _ match a single character
    - SELECT name
    - FROM people
    - WHERE name LIKE 'Ev_';
      - Fill the next letter
      - '_ _ t%' find the record with third letter 't'
- NOT LIKE

  - records that don't match the pattern
    - SELECT name
    - FROM people
    - WHERE name NOT LIKE 'A.%';
- IN

  - allow specify multiple values in a WHERE clause
    - SELECT title
    - FROM films
    - WHERE release_year IN (1920, 1930, 1940);
    - WHERE country IN ('Germany', 'France');SELECT COUNT(DISTINCT title) AS nineties_english_films_for_teens

  #### Example:
- SELECT COUNT(DISTINCT title) AS nineties_english_films_for_teens
  FROM films
  WHERE release_year BETWEEN 1990 AND 1999
  AND language = 'English'
  AND certifications IN ('G', 'PG', 'PG-13');
- IS NULL

  - missing values
- IS NOT NULL

  - have anything
