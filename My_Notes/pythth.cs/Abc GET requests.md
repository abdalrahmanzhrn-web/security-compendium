---
tags: [ "python", "requests", "web-hacking", "automation", "http" ]
aliases: [ "HTTP Requests", "Python Web Scanning" ]
created: 2025-12-21
---

# 🌐 Web Requests with Python

> [!info] The Library
> `requests` allows you to send HTTP requests easily. It handles cookies, headers, and form data without needing to manually manage sockets.

## 1. Basic GET Request
This script fetches the content of a webpage and checks the server's response.

- 1. Define the target URL
- 2. Send the GET request
- 3. Analyze the output
- Status Code: 200 (OK), 404 (Not Found), 403 (Forbidden), etc.
- Text: The raw HTML source code of the page

```python title:web_request.py
import requests

url = "[http://www.vulnweb.com/](http://www.vulnweb.com/)"

response = requests.get(url)

print(f"Status Code: {response.status_code}")

print(response.text)
```

## 📝 Common Status Codes for Pentesting

When building a directory brute-forcer or scanner, you focus on these:
|**Code**|**Meaning**|**Cyber Significance**|
|---|---|---|
|**200**|OK|Page exists and is accessible.|
|**301/302**|Redirect|Might lead to a login page or hidden area.|
|**403**|Forbidden|Potential sensitive directory (WAF or Permissions).|
|**404**|Not Found|Nothing here; move to next payload.|
|**500**|Server Error|Might indicate a successful SQLi or crash.|
