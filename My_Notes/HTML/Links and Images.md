---
tags: [ "html", "web-dev", "links", "images", "phishing-prep" ]
aliases: [ "Hyperlinks", "Attributes" ]
created: 2025-12-21
---

# 🔗 Links and Images

## 1. Hyperlinks (`<a>`)
The anchor tag is used to create links. The `href` attribute defines the destination.

```html
<a href="[https://google.com](https://google.com)">Click here for Google</a>

<a href="[https://google.com](https://google.com)" target="_blank">Open Google in new tab</a>
```

[!danger] Phishing Tip In phishing, attackers often use "Visual Deception." The text says `www.bank.com`, but the `href` leads to `www.evil-bank.com`. Always hover over a link to see the real destination!

## 2. Images (`<img>`)

Images are "self-closing" tags, meaning they don't need a `</img>`.

| **Attribute**    | **Purpose**                                                            |
| ---------------- | ---------------------------------------------------------------------- |
| `src`            | The path to the image file (URL or local path).                        |
| `alt`            | Text that appears if the image fails to load (good for accessibility). |
| `width`/`height` | Sets the size of the image in pixels.                                  |

```html
<img src="[https://example.com/logo.png](https://example.com/logo.png)" alt="Company Logo" width="200" height="100">
```
