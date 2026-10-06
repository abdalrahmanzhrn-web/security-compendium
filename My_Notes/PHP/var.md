---
tags: [ "php", "html", "basics", "variables", "concatenation" ]
aliases: [ "Embedded PHP", "PHP Echo" ]
created: 2025-12-21
---

# 🧬 Mixing HTML and PHP

## 1. The Execution Flow
1. The web server sees the `.php` extension.
2. It reads the HTML normally until it hits `<?php`.
3. It executes the logic (assigning the variable and joining the strings).
4. It replaces the PHP block with the final text and sends it to your screen.

## 2. Code Breakdown

- 1. Variable Assignment
- 2. Concatenation using the dot (.)
- We include "<br>" (HTML line break) inside the string to separate lines

```php title:index.php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>FirstNaho News</title>
</head>
<body>

<p> hi tabbuy </p>
<?php

$boogy = "red";

 echo "chito is " . $boogy . "<br>";
 echo "tabby is " . $boogy;
?>

</body>
</html>
```

- **The Semicolon (`;`):** Every line of PHP logic **must** end with a semicolon. If you forget it, the whole page will crash (White Screen of Death).

- **Concatenation (`.`):** In Python, we used `+` or `,` to join strings. In PHP, we use the **dot**.

- **HTML inside Echo:** You can echo HTML tags (like `<br>`) directly from PHP to control how the text looks on the page.
