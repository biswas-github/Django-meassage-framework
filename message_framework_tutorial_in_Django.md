# Django Message Framework – Beginner Friendly Tutorial

This tutorial explains **Django Message Framework** step‑by‑step with **clear examples** so that _everyone understands_, even if you are learning Django for the first time.

---

## 1. What is Django Message Framework?

The **Message Framework** in Django is used to show **temporary messages (notifications)** to users.

These messages are usually shown **after an action**, such as:

- Login
- Logout
- Form submission
- Create / Update / Delete operations

📌 **Important:**

- Messages are shown **only once**
- After page refresh → message disappears

---

## 2. Why do we need Message Framework?

In Django, after an action, we often use **redirect()**.

Example:

```python
return redirect('home')
```

After redirect:

- You **cannot pass normal variables** like context
- But you still want to show feedback to the user

✅ Message Framework solves this problem.

---

## 3. Real-life Analogy 🧠

Think of Message Framework as:

> A **temporary notice** given to a user that disappears after reading.

---

## 4. Check Required Settings (Very Important)

Django enables Message Framework by default.

### `settings.py`

```python
INSTALLED_APPS = [
    'django.contrib.messages',
]

MIDDLEWARE = [
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
]
```

If these are present → you are ready ✅

---

## 5. Import Messages in View

In `views.py`:

```python
from django.contrib import messages
```

This allows Django to send messages.

---

## 6. Display Messages in Template (MOST IMPORTANT)

Add this code **once**, usually in `base.html`.

```html
{% if messages %} {% for message in messages %}
<p>{{ message }}</p>
{% endfor %} {% endif %}
```

Now messages will show on all pages using `base.html`.

---

## 7. Types of Messages in Django

Django provides **five types** of messages.

---

## 7.1 Success Message ✅

Used when an action is completed successfully.

### View Example

```python
messages.success(request, "Data saved successfully")
```

### Use Case

- Form submitted
- Account created
- Login successful

---

## 7.2 Error Message ❌

Used when something goes wrong.

### View Example

```python
messages.error(request, "Invalid username or password")
```

### Use Case

- Wrong login credentials
- Form validation error
- Permission denied

---

## 7.3 Warning Message ⚠️

Used to alert the user about a potential issue.

### View Example

```python
messages.warning(request, "Your password will expire soon")
```

### Use Case

- Security warning
- Unsaved changes

---

## 7.4 Info Message ℹ️

Used to give general information.

### View Example

```python
messages.info(request, "Profile updated, but email not verified")
```

### Use Case

- Informational messages
- Neutral updates

---

## 7.5 Debug Message 🛠️

Used mainly for developers.

### View Example

```python
messages.debug(request, "Debug mode is ON")
```

### Use Case

- Development only
- Not shown in production usually

---

## 8. Full Example (View + Redirect)

```python
from django.shortcuts import redirect
from django.contrib import messages

def delete_item(request):
    messages.success(request, "Item deleted successfully")
    return redirect('item_list')
```

---

## 9. Styling Messages Using Tags (Recommended)

Each message has a **tag** like `success`, `error`, etc.

### Template

```html
{% for message in messages %}
<div class="{{ message.tags }}">{{ message }}</div>
{% endfor %}
```

### CSS Example

```css
.success {
  color: green;
}
.error {
  color: red;
}
.warning {
  color: orange;
}
.info {
  color: blue;
}
```

---

## 10. Where are Messages Stored?

- Stored in **session or cookies**
- Automatically managed by Django
- Deleted after being displayed once

---

## 11. Message vs Context (Very Important)

| Context                 | Messages               |
| ----------------------- | ---------------------- |
| Same page data          | Next page feedback     |
| Permanent until refresh | One-time only          |
| Used for templates      | Used for notifications |

---

## 12. Flow of Message Framework

```
User Action
   ↓
View sends message
   ↓
Redirect happens
   ↓
Template shows message
   ↓
Message disappears
```

---

## 13. Exam-Oriented Answer (5 Marks)

> Django Message Framework is used to display temporary, one-time notifications to users after performing actions such as login, form submission, or CRUD operations, especially across redirects, without manually handling sessions.

---

## 14. Final Memory Tip 🧠

> **Use context for data** > **Use messages for feedback**

---

✅ You now understand Django Message Framework completely.
