---
tags: [ "php", "file-handling", "backend", "programming" ]
aliases: [ "Reading Files in PHP", "File I/O" ]
created: 2025-12-21
---

# 📂 Reading Files with PHP

PHP uses "handles" to interact with files. You must open the file, perform your action (read or write), and then close it to prevent memory leaks.

## 1. Implementation: Reading a `.txt` File
This script opens a file named `newwords.txt` and prints its entire contents to the browser.

- --- DEBUGGING ---
- Useful during development to see why a file won't open
- 1. OPEN the file
- "r" stands for Read-Only mode
- 2. READ the content
- filesize($filename) ensures we read exactly the amount of data in the file
- Output the text to the webpage
- 3. CLOSE the file
- Crucial for freeing up system resources

```php title:read_file.php
<?php

ini_set('display_errors', 1);
error_reporting(E_ALL);

$filename = "newwords.txt";

$file_handle = fopen($filename, "r");

if ($file_handle) {

    $content = fread($file_handle, filesize($filename));

    echo $content;

    fclose($file_handle);
} else {
    echo "Error: Could not open the file.";
}
?>
```
