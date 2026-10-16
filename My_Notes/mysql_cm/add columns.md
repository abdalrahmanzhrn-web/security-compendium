---
tags: [ "sql", "mysql", "alter", "ddl", "database", "structure" ]
aliases: [ "Add Column", "Alter Table" ]
created: 2025-12-21
---

# 🔧 Modifying Table Structure (ALTER)

> [!info] Use Case
> Used to change the structure of an existing table without deleting it. The most common task is adding a missing column.

## 1. Adding a New Column
This adds the `Email` column to the end of the `Customers` table.

- Syntax: ALTER TABLE <table_name> ADD <column_name> <data_type>;

```sql title:Add_Column
ALTER TABLE Customers
ADD Email varchar(255);
```
