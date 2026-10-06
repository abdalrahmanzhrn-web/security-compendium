---
tags: [ "php", "mysql", "databases", "backend", "mysqli" ]
aliases: [ "DB Connection", "MySQLi Setup" ]
created: 2025-12-21
---

# 🗄️ PHP Database Connection (MySQLi)

To interact with a database, PHP uses the `mysqli` (MySQL Improved) extension. This allows you to create a connection "object" that stays open while your script runs.

## 1. Connection Script
This script defines the credentials and attempts to open a tunnel to the database.

- Usually 'localhost' or '127.0.0.1'
- Default administrative user
- The password (often blank or 'toor' in Kali)
- The specific database you want to use
- 1. Create the Connection Object
- 2. Error Handling
- The 'die' function stops the script immediately if something goes wrong.
- 3. User Input (Commented out)
- This is how you would eventually capture data to send to the DB

```php title:db_connect.php
<?php

$servername = "localhost";
$username = "root";
$password = "toor";
$dbname = "Users";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

echo "connect is made";

?>
```

## 📝 Key Security Observations

- **Hardcoded Credentials**: Storing the username (`root`) and password (`toor`) directly in the file is common for tutorials but dangerous in production.

- **The `die()` Function**: This is a common PHP pattern. If the condition is true, it prints the message and kills the process to prevent further code execution.

- **Connection Object**: The variable `$conn` is now your "handle." Any time you want to search, add, or delete data from the database later, you will use this `$conn` variable.
