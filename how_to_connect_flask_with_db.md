
# 📝 Flask Todo App with SQLAlchemy (SQLite)

A beginner-friendly Flask project that uses SQLAlchemy ORM with SQLite to manage a simple TODO app.

---

## ✅ Step-by-Step Setup: Flask + SQLAlchemy Todo App

---

### 📁 1. Project Structure

```bash
flask-todo-app/
│
├── static/
│   └── css/
│       └── styles.css        # Your frontend CSS files (optional)
│
├── templates/
│   └── index.html            # HTML templates using Jinja2
│
├── app.py                    # Main Flask app file
├── create_db.py              # Script to create the database
├── todo.db                   # Generated SQLite DB file (after setup)
├── requirements.txt          # Python dependencies
└── README.md                 # Project instructions
```

---

### 📦 2. Install Python Packages

Create a virtual environment and install dependencies:

```bash
python -m venv venv
source venv/bin/activate        # On Linux/macOS
venv\Scripts\activate           # On Windows

pip install Flask flask_sqlalchemy
```

> You can save dependencies later using:
```bash
pip freeze > requirements.txt
```

---

### ⚙️ 3. Configure `app.py`

Basic Flask + SQLAlchemy setup:

```python
from flask import Flask, render_template
from flask_sqlalchemy import SQLAlchemy 
from datetime import datetime

app = Flask(__name__)

# DB Configuration
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///todo.db'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

# Init DB
db = SQLAlchemy(app)

# Model
class Todo(db.Model):
    sno = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100), nullable=False)
    desc = db.Column(db.String(500), nullable=False)
    created_date = db.Column(db.DateTime, default=datetime.utcnow)

    def __repr__(self) -> str:
        return f"{self.sno} {self.title}"

# Routes
@app.route('/')
def index():
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)
```

---

### 🛠️ 4. Create the Database

Run the following Python script to generate `todo.db`:

```python
# create_db.py

from app import db
db.create_all()
print("✅ Database created successfully!")
```

Then run:

```bash
python create_db.py
```

---

### 🧪 5. Run Your App

Start your Flask server:

```bash
python app.py
```

Now visit:

```
http://127.0.0.1:5000/
```

---

### 🔗 6. Connect Styles in `index.html`

```html
<link rel="stylesheet" href="{{ url_for('static', filename='css/styles.css') }}">
```

> If you’re not using any CSS yet, feel free to leave this out until needed.

---

### 📄 7. Sample `index.html` (optional)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Todo App</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='css/styles.css') }}">
</head>
<body>
  <h1>Welcome to Flask Todo App!</h1>
</body>
</html>
```

---

### ✅ Done!

You’ve now set up a working Flask + SQLAlchemy app with SQLite and are ready to expand with forms, routes, and data manipulation.

---

### 💡 Extra Tips

- You can split the `models.py` if the app grows larger
- Add form handling with Flask-WTF or manually with `request.form`
- Add route for adding/deleting/updating todos

---

Let me know if you'd like:
- Tailwind or Bootstrap integrated  
- Forms for adding/deleting tasks  
- Flask-Migrate for DB versioning  

Happy coding! 🚀
