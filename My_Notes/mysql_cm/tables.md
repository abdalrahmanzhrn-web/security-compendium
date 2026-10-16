---
tags: [ "sql", "mysql", "database", "ddl", "syntax" ]
aliases: [ "Create Table", "SQL Schema" ]
created: 2025-12-21
---

# 🏗️ SQL Table Creation (Detailed)

> [!info] Syntax Structure
> When creating a table, you define the **Column Name** followed by the **Data Type**.

## 1. Example: 'Persons' Table
A standard user-data table structure.

- Integer: Whole numbers (1, 2, 3...)
- Varchar: Variable text up to 255 chars

```sql title:Create_Persons_Table
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
```
