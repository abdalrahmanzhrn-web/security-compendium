---
tags: [ "php", "programming", "functions", "parameters", "basics" ]
aliases: [ "PHP Function Arguments" ]
created: 2025-12-21
---

# 📥 PHP Functions with Parameters

Parameters are like placeholders inside the function parentheses. When you call the function, you provide the actual data (Arguments).

## 1. Implementation
In this example, `$x` and `$y` act as variables that only exist inside the function `myNametest`.

- 1. Define function with two parameters: $x and $y
- You can inject variables directly into double quotes ""
- 2. Call the function and pass the strings (Arguments)

```php title:params.php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>FirstNaho</title>
</head>
<body>

<p> hi tabbuy </p>

<?php

function myNametest($x, $y){

    echo "my name is $x $y";
}

myNametest("zah", "taab");
?>

</body>
</html>
```
