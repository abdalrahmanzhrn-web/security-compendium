---
tags: [ "sql", "mysql", "insert", "dml", "database" ]
aliases: [ "Insert Data", "SQL Insert Into" ]
created: 2025-12-21
---

# 📥 Inserting Data (INSERT INTO)

> [!info] Syntax Modes
> You can either provide values for **every** column in order, or specify **specific** columns to fill.

## 1. Full Row Insertion
If you do not specify column names, you must provide a value for every single column in the exact order the table was created.

- Syntax: INSERT INTO <table> VALUES (val1, val2, val3...);
- Result:
- All columns are filled.
- Syntax: INSERT INTO <table> (column_name) VALUES (value);

```sql title:Insert_All_Values
INSERT INTO Persons VALUES ("5555", "wiroscka", "dorkalb", "shit hole", "birmingham");

INSERT INTO Persons(City) VALUES("washington");
```

## 3. The Result (NULL Values)

When you view the table after a partial insert, notice the `NULL` values for the missing data.

+----------+----------+-----------+-----------+------------+
| PersonID | LastName | FirstName | Address   | City       |
+----------+----------+-----------+-----------+------------+
|     5555 | wiroscka | dorkalb   | shit hole | newyork    |
|     NULL | NULL     | NULL      | NULL      | washington | <--- Partial Insert
+----------+----------+-----------+-----------+------------+
