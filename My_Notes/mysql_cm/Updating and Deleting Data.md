---
tags: [ "sql", "mysql", "update", "delete", "dml", "database", "maintenance" ]
aliases: [ "Modify Data", "Remove Rows" ]
created: 2025-12-21
---

# ✏️ Updating & Deleting Data

> [!danger] CRITICAL WARNING
> **NEVER** run `UPDATE` or `DELETE` without a `WHERE` clause unless you want to wipe or overwrite **every single row** in the table.
> * Bad: `DELETE FROM Persons;` (Deletes everyone)
> * Good: `DELETE FROM Persons WHERE PersonID = 5555;` (Deletes one person)

## 1. Updating Data (Fixing Mistakes)
Used to modify existing records. Let's fix a row where the City is currently "Warsaw" and change it to "London".

- Syntax: UPDATE <table> SET <column> = "new_value" WHERE <condition>;
- Result:
- Only the person with ID 5558 has their city changed.
- Syntax: DELETE FROM <table> WHERE <condition>;
- Result:
- Any row where the ID is missing (NULL) is permanently removed.

```sql title:Update_Row
UPDATE Persons
SET City = "London"
WHERE PersonID = 5558;

DELETE FROM Persons
WHERE PersonID IS NULL;

Always run a `SELECT` afterwards to confirm your changes were correct.

SELECT * FROM Persons;
```
