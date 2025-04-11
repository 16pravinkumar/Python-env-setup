

```markdown
# 🐍 Python Environment Setup Guide

A simple cheat sheet to set up and manage your Python environment effectively.

```

---

## 📦 Install a Package

```bash
pip install package_name
```

---

## 📋 List All Installed Packages

```bash
pip list
```

---

## 🧪 Create a Virtual Environment

```bash
virtualenv env
```

---

## 🔛 Activate Virtual Environment (Windows)

```bash
.\env\Scripts\activate
```

## ▶️ Run a Python Script

```bash
python app.py
```
---
## Write down this basic route setup in app.py

```bash
# Importing necessary modules from the Flask package
from flask import Flask, render_template, request

# Creating a Flask application instance
app = Flask(__name__)

# Defining the route for the homepage ('/') and the corresponding view function
@app.route('/')
def index():
    return "Hello World"  # Returns a simple response when the homepage is accessed

# This ensures the app runs only when this script is executed directly (not imported)
if __name__ == "__main__":
    app.run(debug=True)  # Starts the Flask development server with debug mode ON

```

---

## 📤 Export Installed Packages

```bash
pip freeze > requirements.txt
```

---

## 📥 Install Packages from requirements.txt

```bash
pip install -r requirements.txt
```

## 🔚 Deactivate Virtual Environment

```bash
deactivate
```

---

## 🧠 Type Checking with mypy

```bash
mypy file.py
```

> ⚠️ `mypy` must be installed (`pip install mypy`) to use this command.



