---
tags: [ "php", "programming", "functions", "basics" ]
aliases: [ "PHP Function Basics" ]
created: 2025-12-21
---

# 🛠️ PHP Functions

Functions are blocks of code that "sit and wait" until they are called. They help keep your code organized and dry (Don't Repeat Yourself).

## 1. Function Syntax
In PHP, you define a function using the `function` keyword, followed by the name and curly braces `{}`.

- 1. Defining the function
- 2. Calling the function

```php title:functions.php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>FirstNaho News</title>
</head>
<body>

<p> hi tabbuy </p>

<?php

function test(){
    echo "this is a test";
}

test();
?>

</body>
</html>
```

## 📝 Key Rules for PHP Functions

- **Naming:** Function names are **not** case-sensitive (unlike variables!), but it is best practice to keep them consistent.

- **Execution:** The code inside the function will not run until the line `test();` is reached.

- **Placement:** In PHP, you can call a function before it is defined in the script, but usually, programmers define them at the top or in a separate file.

| **Feature**     | **Python**                | **PHP**            |
| --------------- | ------------------------- | ------------------ |
| **Keyword**     | `def`                     | `function`         |
| **Blocks**      | Indentation (tabs/spaces) | Curly Braces `{ }` |
| **End of Line** | New line                  | Semicolon `;`      |
