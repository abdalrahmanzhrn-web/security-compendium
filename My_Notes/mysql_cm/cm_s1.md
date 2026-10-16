---
tags: [ "mysql", "mariadb", "sql", "database", "syntax", "cheatsheet" ]
aliases: [ "SQL Commands", "MariaDB CLI" ]
created: 2025-12-21
---

# 🐬 MySQL / MariaDB Command Line Syntax

> [!info] Context
> These commands are run directly inside the MySQL/MariaDB shell (`mysql >` or `MariaDB [(none)]>`).

## 1. System Enumeration
Basic commands to check where you are and what version is running.

- Single line check
- Multi-line formatting (Clean output)
- List all databases
- Select a database to use
- List tables in the current database
- 1. Create a new database
- 2. Create a table with columns
- Syntax: CREATE TABLE <name> (col1 TYPE, col2 TYPE...);
- 3. Verify table structure
- Insert manual data
- Read everything from the table
- Load a local text file into the table

```sql title:System_Checks
SELECT VERSION();
SELECT NOW();
SELECT CURRENT_DATE();

SELECT
    USER(),
    CURRENT_DATE(),
    VERSION();

SHOW DATABASES;

USE empire;

SHOW TABLES;

CREATE DATABASE chico;
USE chico;

CREATE TABLE TABBY (
    names VARCHAR(10),
    sleep DATE,
    SHIT DATE
);

DESCRIBE TABBY;

INSERT INTO TABBY VALUES ('CHIIIITO', '2022-01-01', '2023-01-01');

SELECT * FROM TABBY;

LOAD DATA INFILE '/home/chico/chito.txt' INTO TABLE TABBY;
```
