# Foundations  
*By Lukas Van der Spiegel (Author)*

This chapter provides a compact recap of essential SQL concepts: how relational databases are structured, how SQL queries work, and how to write correct and efficient statements.

---

## What Is an RDBMS?

A relational database stores data in structured tables with:

- Tables  
- Columns (fields)  
- Rows (records)  
- Primary keys  
- Foreign keys  
- Relations  
- Indexes (speed up lookups)

An RDBMS (Relational Database Management System) manages these databases (e.g., PostgreSQL, MySQL, SQL Server).



## PostgreSQL Data Hierarchy

Cluster → Database → Schema → Table → Rows & Columns

- Cluster contains databases  
- Database contains schemas  
- Schema contains tables, views, functions  
- Table contains rows and columns  

Search path: determines which schemas are searched when no schema is specified.  
Example:  
SET search_path TO space_travel, tennis;



## SQL Language Areas

- **DDL *(Data Definition Language)*** — Create/alter schemas & tables  
- **DML *(Data Manipulation Language)*** — Insert, update, delete data  
- **DQL *(Data Query Language)*** — Select (read)  
- **DCL *(Data Control Language)*** — Permissions (GRANT/REVOKE)  
- **TCL *(Transaction Control Language)*** — Transactions (COMMIT/ROLLBACK)

SQL has dialects (PostgreSQL, T‑SQL, PL/SQL, MySQL, SQLite).



## 4. SELECT Statement Structure

A SELECT query uses these clauses:

- SELECT  
- FROM  
- WHERE  
- GROUP BY  
- HAVING  
- ORDER BY  
- OFFSET  
- FETCH  

The order cannot be changed.



## SELECT Execution Flow

1. FROM — identify source tables  
2. WHERE — filter rows  
3. GROUP BY — group rows  
4. HAVING — filter groups  
5. SELECT — choose output columns  
6. ORDER BY — sort rows  
7. OFFSET — skip rows  
8. FETCH — limit rows  



## From Question to SQL

Example question:  
“Which celestial objects have a diameter ≥ 100,000 km?”

```sql
SELECT objectname, diameter, distance
FROM celestial_object
WHERE diameter >= 100000
ORDER BY objectname, diameter;
```

## Resultsets

A resultset is a temporary table produced by a query.

Types:

- Full resultset — many rows, many columns  
- Singleton — exactly 1 row  
- Single cell — 1 row, 1 column  
- Empty resultset — 0 rows (not NULL)



## NULL Values

- Represents missing/unknown data  
- NULL is not equal to an empty string  
- Comparisons with NULL → unknown  
- Aggregates ignore NULL (except COUNT(*))



## WHERE Clause — Search Conditions

- Comparison: =, <, >, AND, OR  
- Range: BETWEEN  
- Set membership: IN  
- Pattern matching: LIKE  
- NULL check: IS NULL



## Aggregate Functions

- COUNT  
- SUM  
- AVG  
- MIN  
- MAX

Example:
```sql
SELECT COUNT(*) FROM celestial_object;
```


## GROUP BY and HAVING

GROUP BY groups rows.  
HAVING filters groups.

Example:
```sql
SELECT objectname, duration_of_stay, COUNT(*) AS visits
FROM visit
GROUP BY objectname, duration_of_stay
HAVING COUNT(*) >= 2;
```


## DISTINCT

Removes duplicates.

```sql
SELECT DISTINCT objectname FROM visit;
```



## CASE Expressions
```sql
SELECT objectname,
    CASE
        WHEN satellite_of IS NULL THEN 'Star'
        WHEN satellite_of = 'Sun' THEN 'Planet'
        ELSE 'Satellite'
    END AS objecttype
FROM celestial_object;
```

## Joins

Implicit join (old style):

```sql
SELECT c.client_nr, c.lastname, p.journey_nr
FROM client c, participation p
WHERE c.client_nr = p.client_nr;
```

Explicit join (recommended):

```sql
SELECT c.client_nr, c.lastname, p.journey_nr
FROM client c
INNER JOIN participation p ON c.client_nr = p.client_nr;
```

Join types:

- INNER JOIN  
- LEFT OUTER JOIN  
- RIGHT OUTER JOIN  
- FULL OUTER JOIN  
- CROSS JOIN  

Example (LEFT JOIN):

```sql
SELECT c.client_nr, c.lastname, p.journey_nr
FROM client c
LEFT JOIN participation p ON c.client_nr = p.client_nr;
```


## UNION and UNION ALL

Combine resultsets.

Rules:
- Same number of columns  
- Compatible types  
- Column names come from first query  

Example:

```sql
SELECT objectname FROM stars
UNION
SELECT objectname FROM planets;
```


## CREATE TABLE

```sql
CREATE TABLE visit (
    journey_nr NUMERIC(4) NOT NULL,
    objectname VARCHAR(10),
    sequence_number NUMERIC(2) NOT NULL,
    duration_of_stay NUMERIC(4),
    PRIMARY KEY (journey_nr, sequence_number),
    FOREIGN KEY (journey_nr) REFERENCES journey(journey_nr),
    FOREIGN KEY (objectname) REFERENCES celestial_object(objectname)
);
```

Common constraints:

- PRIMARY KEY  
- NOT NULL  
- UNIQUE  
- DEFAULT  
- CHECK  
- FOREIGN KEY  



## GRANT / REVOKE

```sql
GRANT SELECT ON visit TO analyst;
REVOKE UPDATE ON celestial_object FROM trainee;
```

# INSERT

```sql
INSERT INTO client (client_nr, lastname, firstname)
VALUES (127, 'Jobs', 'Steve');
```    

Insert from another table:

```sql
INSERT INTO table2 (col1, col2)
SELECT col1, col2 FROM table1;
``` 


## UPDATE

```sql
UPDATE visit
SET duration_of_stay = duration_of_stay + 1
WHERE objectname = 'Mars';
``` 

Update using another table:

```sql
UPDATE celestial_object AS co
SET distance = co.distance * 0.98
FROM visit v
WHERE co.objectname = v.objectname;
``` 

## DELETE

```sql
DELETE FROM client
WHERE lastname = 'Jobs' AND firstname = 'Steve';
``` 

Always use WHERE — otherwise all rows are deleted.