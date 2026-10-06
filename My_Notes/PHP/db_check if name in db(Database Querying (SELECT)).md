---
tags: [ "php", "mysql", "sql-injection", "backend", "mysqli" ]
aliases: [ "SQL Selection", "Database Querying" ]
created: 2025-12-21
---

# 🔍 Querying the Database (SELECT)

Once the connection is established, we use **SQL (Structured Query Language)** to communicate with the database. The `SELECT` statement is used to fetch data.

## 1. The Logic Flow
This script takes a name from a web form and checks if that name exists in the `cred` table.

- 1. Setup Connection (Reusing your credentials)
- 2. Capture the User Input
- Taking the 'name' field from an HTML form
- 3. Construct the SQL Query
- We are asking: "Find everything (*) from the 'cred' table where the Name column matches"
- 4. Run the Query
- 5. Check the Result
- num_rows tells us how many matching users were found
- Always close your connection

```php title:check_user.php
<?php

$servername = "localhost";
$username = "root";
$password = "toor";
$dbname = "Users";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$name_to_check = $_POST["name"];

$sql = "SELECT * FROM cred WHERE Name = '$name_to_check'";

$result = $conn->query($sql);

if ($result->num_rows > 0) {

    echo "The user " . $name_to_check . " is present.";
} else {
    echo "He's not.";
}

$conn->close();
?>
```
