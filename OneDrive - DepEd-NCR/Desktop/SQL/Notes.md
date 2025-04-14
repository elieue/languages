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
