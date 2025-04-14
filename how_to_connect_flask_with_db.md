 Setting up SQLAlchemy in Flask is one of the most powerful ways to integrate a database with your app — and it’s pretty straightforward too. Here's a clean step-by-step guide for you.

✅ Step-by-Step: Setting Up SQLAlchemy in Flask
🧱 1. Install Flask + SQLAlchemy
bash
Copy
Edit
pip install Flask
pip install flask_sqlalchemy
📁 2. Create a Flask App Folder Structure
bash
Copy
Edit
your_project/
│
├── app.py
├── models.py
├── templates/
├── static/
└── config.py   ← (optional, for cleaner DB setup)
📝 3. Create app.py
python
Copy
Edit
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)

# DB Configuration
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///mydatabase.db'  # or use MySQL/Postgres
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

# Init DB
db = SQLAlchemy(app)

# Import your models
from models import User

@app.route('/')
def home():
    return 'Flask + SQLAlchemy is working!'

if __name__ == '__main__':
    app.run(debug=True)
🧬 4. Create models.py
python
Copy
Edit
from app import db

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(100), nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)

    def __repr__(self):
        return f'<User {self.username}>'
🔧 5. Create the Database
Now that everything is set up:

bash
Copy
Edit
python
>>> from app import db
>>> db.create_all()
This creates the mydatabase.db file with the User table.

🧪 6. Test by Adding a User (optional)
python
Copy
Edit
>>> from models import User
>>> new_user = User(username='pravinkumar', email='pravin@example.com')
>>> db.session.add(new_user)
>>> db.session.commit()
