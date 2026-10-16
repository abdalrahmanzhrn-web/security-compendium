---
tags: [ "sql", "mysql", "select", "where", "dql", "database" ]
aliases: [ "Filter Rows", "SQL Where Clause" ]
created: 2025-12-21
---

# 🔍 Searching in Tables (WHERE Clause)

> [!info] Logic
> The `WHERE` clause filters the results. Instead of dumping the whole table, it only returns rows that match your specific condition.

## 1. Basic Filtering
This query asks the database to show **all columns** (`*`) but **only for the rows** where the City is "Warsaw".

- Syntax: SELECT * FROM <table_name> WHERE <column> = "value";

```sql title:Select_Where
SELECT * FROM Persons WHERE City = "Warsaw";
```

## Output Analysis

Notice that even though the table might have hundreds of people, the result only shows the 3 matches.

+----------+------------+-----------+------------+--------+
| PersonID | LastName   | FirstName | Address    | City   |
+----------+------------+-----------+------------+--------+
|     NULL | NULL       | NULL      | NULL       | Warsaw |
|     5558 | john       | kalb      | shit place | Warsaw |
|    65698 | shevshenko | Alexandra | hole       | Warsaw |
+----------+------------+-----------+------------+--------+
