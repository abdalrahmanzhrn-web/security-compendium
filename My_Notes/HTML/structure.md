---
tags: [ "html", "web-dev", "basics", "structure" ]
aliases: [ "HTML Skeleton", "Text Formatting" ]
created: 2025-12-21
---

# 🏗️ HTML Document Structure

> [!info] The Basics
> HTML (HyperText Markup Language) uses **tags** to define content. Most tags have an opening `<tag>` and a closing `</tag>`.

## 1. The Core Skeleton
Every HTML page follows this standard hierarchy.

```html title:structure.html
<!DOCTYPE html> <html lang="en"> <head>
    <meta charset="UTF-8"> <title>FirstNaho News</title> </head>
<body>
    </body>
</html>
```

## 2. Headings and Hierarchy

Headings range from `<h1>` (most important) to `<h6>` (least important).

- **`<h1>`**: Main title of the page.

- **`<h2>`**: Section headers.

- **`<h3>`**: Sub-sections.

## 3. Text Formatting Tags

Your note introduces three important ways to display text:

| **Tag** | **Purpose**     | **Feature**                                                           |
| ------- | --------------- | --------------------------------------------------------------------- |
| `<p>`   | Paragraph       | Standard text block with automatic spacing.                           |
| `<pre>` | Preformatted    | Maintains **exactly** how you typed it (spaces, tabs, and new lines). |
| `<b>`   | Bold            | Makes text **stronger** visually.                                     |
| `<hr>`  | Horizontal Rule | Creates a thematic break (a horizontal line).                         |

```HTML
<h1>Naho News</h1> <h2>Chico section</h2> <h3>Sausages</h3> <pre>
  This text will keep
  its   spacing   exactly
  as written here.
</pre>

<hr> <h2>Tabby section</h2>
<p>This is a standard paragraph where the browser ignores extra spaces.</p>
```
