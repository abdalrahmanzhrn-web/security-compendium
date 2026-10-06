---
tags: [ "php", "file-handling", "logging", "backend" ]
aliases: [ "Writing to Files", "PHP Append" ]
created: 2025-12-21
---

# ✍️ Writing to Files with PHP (Append Mode)

When writing to files, the **mode** you choose is critical. Using `"a"` (Append) is safer than `"w"` (Write) because it adds data to the end of the file instead of wiping the file clean.

## 1. Implementation: Adding a New Line
This script targets `newwords.txt` and adds a custom string to the very bottom.

- The \n creates a new line (Line Break) in the text file
- 1. OPEN file in "a" mode (Append)
- If the file doesn't exist, PHP will try to create it automatically.
- 2. WRITE the text to the file handle
- 3. CLOSE to save changes and free memory
- Common error: The web server (www-data) doesn't have write permissions

```php title:append_file.php
<?php
$filename = "newwords.txt";

$text_to_add = "I am adding this new line to the bottom.\n";

$file_handle = fopen($filename, "a");

if ($file_handle) {

    fwrite($file_handle, $text_to_add);

    fclose($file_handle);

    echo "Success: Text added to the file.";
} else {

    echo "Error: Could not open file. Check permissions!";
}
?>
```
