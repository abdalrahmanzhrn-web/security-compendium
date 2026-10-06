---
tags: [ "php", "web-dev", "best-practices", "modularity" ]
aliases: [ "PHP Include", "DRY Principle" ]
created: 2025-12-21
---

# 🧩 Modular PHP: The Include Method

> [!tip] The DRY Principle
> **D.R.Y** stands for **Don't Repeat Yourself**. Instead of copy-pasting the database connection code into every file, you store it in one place and "include" it where needed.

## 1. The Connection File (`db_connect.php`)
This file contains only the setup and the `$conn` variable.

- Note: No echo here to keep your other pages clean!

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

?>
```

## 2. The Main Action File (`register.php`)

By using `include`, all variables from `db_connect.php` (like `$conn`) become available here automatically.

- 1. Pull in the connection logic
- 2. Start immediately with Step 2: Capture Data
- 3. Run the Query using the $conn variable from the included file

```php
<?php

include 'db_connect.php';

$username = $_POST["name"];
$email = $_POST["email"];
$password = $_POST["password"];

$sql = "INSERT INTO cred (Name, Email, Password) VALUES ('$username', '$email', '$password')";

if ($conn->query($sql) === TRUE) {
    echo "New record created successfully";
}

$conn->close();
?>
```
