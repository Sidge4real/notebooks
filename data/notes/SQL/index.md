# Introduction
SQL (Structured Query Language) is a powerful language used for managing and manipulating relational databases. It allows users to create, read, update, and delete data in a structured format. SQL is widely used in various applications, from small-scale projects to large enterprise systems.
## Core SQL Types
1. **Data Definition Language (DDL)** – commands to define or modify database structure  
2. **Data Manipulation Language (DML)** – commands to insert, update, delete, or query data
3. **Data Control Language (DCL)** – commands to control access to data (e.g., GRANT, REVOKE)
4. **Transaction Control Language (TCL)** – commands to manage transactions (e.g., COMMIT, ROLLBACK)
5. **Persistent Stored Modules (PSM)** – commands to create and manage stored procedures, functions, and triggers

## 1. Data Definition Language (DDL)
- **CREATE**: Create a new table, view, or other database object
- **ALTER**: Modify an existing database object (e.g., add a column to a table)
- **DROP**: Delete an existing database object
- **TRUNCATE**: Remove all records from a table, but keep the structure
## 2. Data Manipulation Language (DML)
- **SELECT**: Retrieve data from one or more tables
- **INSERT**: Add new records to a table
- **UPDATE**: Modify existing records in a table
- **DELETE**: Remove records from a table
## 3. Data Control Language (DCL)
- **GRANT**: Give users access privileges to the database
- **REVOKE**: Remove access privileges from users
## 4. Transaction Control Language (TCL)
- **COMMIT**: Save all changes made in the current transaction
- **ROLLBACK**: Undo all changes made in the current transaction
- **SAVEPOINT**: Set a savepoint within a transaction to which you can later roll back

## 5. Persistent Stored Modules (PSM)
- **Stored Procedures**: Predefined SQL code that can be executed with parameters
- **Functions**: Similar to stored procedures but return a value
- **Triggers**: Automatically execute a specified action in response to certain events on a table or view

----

# SQL Syntax and Conventions
## Basic SQL Syntax
- SQL statements are case-insensitive (e.g., `SELECT` and `select` are the same)
- SQL statements typically end with a semicolon (`;`)
- Keywords (e.g., `SELECT`, `FROM`, `WHERE`) are often written in uppercase for readability
- Identifiers (e.g., table names, column names) can be case-sensitive depending on the database system
## Common SQL Conventions
- Use meaningful names for tables and columns
- Use indentation and line breaks to improve readability
- Comment your SQL code to explain complex logic or decisions
- Avoid using reserved keywords as identifiers (e.g., `SELECT`, `TABLE`)
- Use parameterized queries to prevent SQL injection attacks
- Always test your SQL queries on a small dataset before running them on production data
- Use transactions to ensure data integrity when performing multiple related operations
- Regularly back up your database to prevent data loss
- Optimize your queries for performance by using indexes and avoiding unnecessary calculations
- Keep your SQL code organized and modular by using views, stored procedures, or functions where appropriate

----
## SQL Database Systems
There are many SQL database systems available, each with its own features and capabilities. Some of the most popular SQL database systems include:

1. **MySQL** – an open-source relational database management system (RDBMS)
2. **PostgreSQL** – an open-source RDBMS known for its advanced features and extensibility
3. **Microsoft SQL Server** – a commercial RDBMS developed by Microsoft
4. **Oracle Database** – a commercial RDBMS developed by Oracle Corporation
5. **SQLite** – a lightweight, file-based RDBMS often used in embedded systems and mobile applications
6. **MariaDB** – a fork of MySQL, offering additional features and improvements
7. **Amazon RDS** – a cloud-based relational database service provided by Amazon Web Services (AWS)
8. **Google Cloud SQL** – a fully-managed relational database service provided by Google Cloud Platform (GCP)
9. **Azure SQL Database** – a cloud-based relational database service provided by Microsoft Azure
10. **CockroachDB** – a distributed SQL database designed for high availability and scalability
11. **Snowflake** – a cloud-based data warehousing platform that supports SQL queries
12. **Redshift** – a cloud-based data warehousing service provided by Amazon Web Services
13. **Vertica** – a columnar storage platform designed for big data analytics
14. **Greenplum** – an open-source, distributed database designed for big data analytics
15. **IBM Db2** – a family of data management products, including RDBMS and data warehousing solutions
16. **SAP HANA** – an in-memory, column-oriented RDBMS developed by SAP
17. **Teradata** – a data warehousing solution designed for large-scale analytics
18. **Apache Hive** – a data warehouse software built on top of Hadoop for querying and managing large datasets using SQL-like syntax
19. **Presto** – an open-source distributed SQL query engine for big data analytics
20. **Apache Impala** – a high-performance distributed SQL engine for big data analytics
21. **ClickHouse** – a columnar database management system designed for online analytical processing (OLAP)
22. **TimescaleDB** – an open-source time-series database built on PostgreSQL
23. **InfluxDB** – an open-source time-series database designed for high-performance data ingestion and querying
24. **Apache Phoenix** – a SQL skin over HBase for low-latency queries
25. **Google BigQuery** – a fully-managed, serverless data warehouse that supports SQL queries
...