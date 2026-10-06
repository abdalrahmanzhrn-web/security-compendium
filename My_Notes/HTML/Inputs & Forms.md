# Inputs & Forms

### 1. The Form Container

The `<form>` tag wraps all inputs. The `action` is where the data is sent, and `method` is usually "POST" for sensitive data.

```html
<form action="/login.php" method="POST">
    </form>
```

### 2. Common Input Types

Each input needs a `type` (how it looks) and a `name` (the variable name the server sees).

```html
<label>Username:</label>
<input type="text" name="username" placeholder="Enter username">

<label>Password:</label>
<input type="password" name="password"> <label>Role:</label>
<input type="radio" name="role" value="admin"> Admin
<input type="radio" name="role" value="user"> User

<input type="submit" value="Login">
```

### 📝 Cyber Context: Form Grabbing

When you are looking at a website's source code to build a brute-forcer:

1. Find the `<form>` tag to see the **URL** in the `action` attribute.

2. Find the `<input>` tags to see the **names** (e.g., `user`, `pass`).

3. This tells you exactly how to build your `payload = {"user": "admin", "pass": "123"}` in Python!
