✅ Folder Structure
```
bash
todo-flask-app/
│
├── app.py                 ← Main Flask app
├── create_db.py           ← Initializes the database
├── models.py              ← (Optional if separated model logic)
├── todo.db                ← (Generated after running create_db.py)
├── templates/
│   └── index.html         ← Frontend HTML file
├── static/
│   └── (css, js, images)  ← Public assets if needed
├── README.md              ← Instructions
└── requirements.txt       ← (Optional - Python dependencies)
```

```
📄 create_db.py — Database Creator
python
Copy
Edit
from app import db
db.create_all()
print("✅ Database created successfully!")
This script imports the db object from app.py and calls create_all() which creates the todo.db file with the Todo table inside.
```

```
📝 README.md
markdown
Copy
Edit
# 📝 Flask Todo App (with SQLAlchemy)

A simple Flask To-Do app using SQLite and SQLAlchemy as the ORM.
```
---

## 📁 Folder Structure
```
todo-flask-app/ ├── app.py # Main Flask app ├── create_db.py # Script to initialize the database ├── todo.db # (Auto-generated SQLite DB) ├── templates/ │ └── index.html # HTML file rendered by Flask ├── static/ # Public assets (CSS/JS/images) └── README.md # Project setup instructions
```
yaml
Copy
Edit

---

## 🚀 How to Run This App

### 1. Clone the repository / Download the files
```bash
git clone <repo-url>
cd todo-flask-app
2. Create a virtual environment (optional but recommended)
bash
Copy
Edit
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
3. Install dependencies
bash
Copy
Edit
pip install Flask
pip install flask_sqlalchemy
Alternatively, if you have requirements.txt, run:

bash
Copy
Edit
pip install -r requirements.txt
🛠️ Setup the Database
Run the following script to create the SQLite database and required table:

bash
Copy
Edit
python create_db.py
This will generate a todo.db file with a Todo table.

📦 Start the Flask App
bash
Copy
Edit
python app.py
Now visit:
👉 http://127.0.0.1:5000/

🧩 Tech Stack
Python 3.x

Flask

SQLite

SQLAlchemy ORM

📌 Features
Add and display todo items

Save tasks in SQLite database

Simple HTML templating with Jinja2

📬 Author
Pravinkumar Sharma

yaml
Copy
Edit

---

Let me know if you want me to add:
- Forms to create tasks
- Bootstrap styling
- Delete/edit functionality
- REST API version of this app

Happy coding, bro!
