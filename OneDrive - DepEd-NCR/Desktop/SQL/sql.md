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

## Sorting Results

**ORDER BY** - sorts the data in ascending order

**ORDER BY __ DESC** - sorts data in descending order

## Grouping Data

**GROUP BY __** - provide summary when grouping a single field

### Example

Using the `films` table: which `release_year` had the most language diversity?

Take your time to translate this question into code and test your queries in the console.

"Most language diversity" can be interpreted as `COUNT(DISTINCT ___)`. Now over to you.

SELECT release_year, COUNT(DISTINCT language) AS diverse_language

FROM films

GROUP BY release_year

ORDER BY diverse_language DESC

LIMIT 1;

## Filtering Grouped Daata

**HAVING -** keyword for GROUP BY

![1745043528815](image/Notes/1745043528815.png)

WHERE filters individual records, HAVING filters grouped records

# Joining Data in SQL

## Introducing Inner Joins

### The ins and outs of INNER JOIN

INNER JOIN + LEFT JOIN = COMBINED TABLES

ID_field = key

Inner Join = looks for records with the same values in the key field

will return duplicate value

#### Syntax

table.column_name

##### Example:

-- Select fields with aliases

SELECT c.code AS country_code, name, year, e.inflation_rate

FROM countries AS c

-- Join to economies (alias e)

**INNER JOIN** economies AS e

-- Match on code field using table aliases

ON c.code = e.code; || or USING (country)

Defining relationships

One-to-many

One-to-one

Many-to-many

### Multiple Joins

#### Syntax

SELECT * #here mo ilalagay kung anong column want mo

FROM left_table

INNER JOIN right_table

ON left_table.id = right_table.id #here naman yung kaparehas nila na identifier

    AND left_table.date = right_table.id

INNER JOIN another_table

ON left_table.id = another_table.id  # bali you can use using sa same id sa new table na imemerge mo

##### Example:

SELECT p1.country, p2.continent, president, prime_minester, pm_start

FROM prime_minister as p1

INNER JOIN presidents as p2

USING (country)

INNER JOIN prime_minester_terms as p3

USING (prime_minester)

## Outer Joins, Cross Joins and Self Joins

### Left and Right Joins

Bali here sa left join pwede masama lahat ng query kahit hindi match sa right join, pero yung right join yung unmatch is hindi makakasama. Magiging null yung rest ng left join

![1745851176358](image/sql/1745851176358.png)

#### Syntax

SELECT p1.country, prime_minister, president

FROM prime_ministers AS p1

**LEFT JOIN** presidents AS p2 #pwede ring syntax na LEFT OUTER JOIN

USING (country);

Same lang sa RIGHT JOIN, but reverse (RIGHT OUTER JOIN)

### FULL JOINS

return all ids irrespective of whether they have a match, bali null yung mga walang match

#### Syntax

SELECT left_table.id AS L_id, right_table.id AS r_id, left_table.val AS L_val, right_table.val AS R_val

FROM left_table

**FULL JOIN** right_table

USING(id);

##### Example:

SELECT p1.country AS country, prime_minester, president

FROM prime_ministers AS p1

FULL JOIN presidents AS p2

ON p1.country = p2.country

LIMIT 10;

### CROSS JOINS

- creates all possible combinations of two tables

  ![1745935797697](image/sql/1745935797697.png)

#### SYNTAX

SELECT id1, id2

FROM table1

CROSS JOIN table2;

##### Example:

SELECT prime_minester, president

FROM prime_ministers AS p1

CROSS JOIN presidents AS p2 ##KAPAG Cross Join you don't have to use ON or USING

WHERE p1.continent IN ('Asia')

    AND p2.continent IN ('South America')

### SELF JOINS

- table joined with themselves
- can be used to compare parts of the same table

#### SYNTAX

##### EXAMPLE

SELECT p1.country AS country1, p2.country AS country2, p1.continent

FROM prime_ministers AS p1

INNER JOIN prime_ministers AS p2

ON p1.continent = p2.continent

    AND p1.country <> p2.country

LIMIT 10;

# Set Theory for SQL Joins

![1746092430946](image/sql/1746092430946.png)

## Set theory for SQL Joins

UNION - takes two tables as input, and returns all records from both tables not including duplicates

### Syntax

SELECT *

FROM left_table

UNION

SELECT *

FROM right_table;

#### Examples:

SELECT monarch AS leader, country

FROM monarchs

UNION

SELECT prime_ministers, country

FROM  prime_ministers

ORDER BY country, leader

LIMIT 10;

UNION ALL - takes two tables and returns all records from both tables including duplicates

### Syntax

SELECT *

FROM left_table

UNION ALL

SELECT *

FROM right_table;

Note: Do not require "ON" rather than comparing and merging tables on the left and right, they stack fields on top of one another

#### Examples:

SELECT monarch AS leader, country

FROM monarchs

UNION

SELECT prime_ministers, country

FROM  prime_ministers

ORDER BY country, leader

LIMIT 10;

Note: Use the first column name when using ORDER BY

## At the INTERSECT

### Syntax

SELECT *

FROM left_table

INTERSECT

SELECT *

FROM right_table;

Note: Will return one value unlike inner join-duplicate

#### Example

SELECT country AS intersect_country

FROM prime_ministers

INTERSECT

SELECT country

FROM presidents;

## EXCEPT

- allows us to identify the records that are present in one table, but not the other

#### Example

SELECT monarch, country

FROM monarchs

EXCEPT

SELECT prime_ministers, country

FROM prime_ministers;

# Subqueries

## Subquerying with semi joins and anti joins

- a semi joins chooses records in the first table where a condition is met in the second table

  ![1746545156169](image/sql/1746545156169.png)

### Example - Semi Join

SELECT presidents, country, continent

FROM presidents

WHERE country **IN**

    (SELECT country

    FROM states

    WHERE indep_year < 1800);

- use list of countries as a filter by embedding it in a further WHERE clause
- Note: this is a subquery

### Example - Anti Join

SELECT presidents, country,

FROM presidents

WHERE country **LIKE** '%America'

    AND  country**NOT IN**

    (SELECT country

    FROM states

    WHERE indep_year < 1800);

## Subqueries inside WHERE and SELECT

- WHERE IN enables us to provides  a list of values filter on
- Second most type of subquery is SELECT clause

### Syntax

SELECT *

FROM some_table

WHERE some_field IN

    (SELECT some_numeric_field

    FROM another_table

    WHERE field2 = some_condition)

#### Example

SELECT *

FROM populations

WHERE year = 2015

-- Filter for only those populations where life expectancy is 1.15 times higher than average

  AND life_expectancy > 1.15 *

  (SELECT AVG(life_expectancy)

   FROM populations

   WHERE year = 2015);


## Subqueries inside FROM

### Syntax

#### Example
