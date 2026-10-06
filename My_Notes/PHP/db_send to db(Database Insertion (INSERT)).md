---
tags: [ "php", "mysql", "databases", "registration", "backend" ]
aliases: [ "SQL Insertion", "Data Entry" ]
created: 2025-12-21
---

# ✍️ Adding Data to the Database (INSERT)

The `INSERT INTO` statement is used to add new rows of data to a table. This is the backbone of any "Sign Up" page on the web.

## 1. The Implementation
This script captures three pieces of information from a form and stores them in the `cred` table.

- --- STEP 1: CONNECTION ---
- --- STEP 2: CAPTURE DATA ---
- Data usually comes from an HTML <form> using the POST method
- --- STEP 3: CONSTRUCT & RUN QUERY ---
- We specify the table name (cred) and the columns (Name, Email, Password)
- If it fails (e.g., duplicate email), it prints the SQL error
- --- STEP 4: CLOSE THE DOOR ---

```php title:register_user.php
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

$username = $_POST["name"];
$email = $_POST["email"];
$password = $_POST["password"];

$sql = "INSERT INTO cred (Name, Email, Password)
        VALUES ('$username', '$email', '$password')";

if ($conn->query($sql) === TRUE) {
    echo "New record created successfully";
} else {

    echo "Error: " . $sql . "<br>" . $conn->error;
}

$conn->close();
?>
```

## 📝 Key Technical Details

- **Column Mapping**: The order of columns in `(Name, Email, Password)` must perfectly match the order of values in `VALUES ('$username', '$email', '$password')`.

- **Data Types**: String values (like names and emails) must be wrapped in single quotes inside the SQL string.

- **Success Check**: Using `=== TRUE` ensures that the code only confirms registration if the database actually accepted the new row.

## 🛡️ Security Note: The "Plaintext" Danger

In this script, the password is being saved exactly as the user typed it (e.g., "joker101").

- **Risk**: If the database is hacked, every user's password is leaked immediately.

- **Fix**: In a real project, you would use `password_hash()` in PHP to scramble the password before saving it.
