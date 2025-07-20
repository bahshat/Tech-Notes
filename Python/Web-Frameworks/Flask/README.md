
---

## 🌐 Flask Interview Notes

---

### 1. **What is Flask?**

* Lightweight, WSGI-based Python web framework.
* Microframework: minimal by design, extensible via plugins.
* Ideal for REST APIs and small-to-medium web apps.

---

### 2. **Core Concepts**

| Concept          | Description                                                        |
| ---------------- | ------------------------------------------------------------------ |
| WSGI             | Web Server Gateway Interface (standard for Python web apps)        |
| Routing          | URL → Function mapping                                             |
| Request/Response | Handled via `flask.request` and `flask.Response`                   |
| App Factory      | Function that creates app instance (for testing/config separation) |
| Blueprints       | Modularize app by features/routes                                  |

---

### 3. **Basic Flask App**

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello, World!"

if __name__ == '__main__':
    app.run(debug=True)
```

---

### 4. **Route Parameters**

```python
@app.route('/user/<username>')
def show_user(username):
    return f"User: {username}"
```

---

### 5. **Request and Response**

```python
from flask import request, jsonify

@app.route('/data', methods=['POST'])
def get_data():
    json_data = request.get_json()
    return jsonify(json_data)
```

---

### 6. **Template Rendering (Jinja2)**

```python
@app.route('/greet/<name>')
def greet(name):
    return render_template('hello.html', name=name)
```

**Jinja2 Example**:

```html
<!-- hello.html -->
<h1>Hello {{ name }}</h1>
```

---

### 7. **Static Files & Config**

```python
app = Flask(__name__, static_folder='static')

app.config['DEBUG'] = True
app.config['SECRET_KEY'] = 'your_key'
```

---

### 8. **Flask Blueprints (Modular App)**

```python
# user_routes.py
from flask import Blueprint
user_bp = Blueprint('user', __name__)

@user_bp.route('/users')
def list_users():
    return "User List"

# main.py
app.register_blueprint(user_bp)
```

---

### 9. **Database Integration**

* Use Flask-SQLAlchemy or plain SQLAlchemy

```python
from flask_sqlalchemy import SQLAlchemy
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///db.sqlite3'
db = SQLAlchemy(app)
```

---

### 10. **Middleware & Hooks**

```python
@app.before_request
def log_request():
    print("Request received")
```

---

### 11. **API with Flask + Marshmallow**

* Marshmallow = Serialization & Validation

```python
from marshmallow import Schema, fields

class UserSchema(Schema):
    name = fields.Str()
    age = fields.Int()
```

---

### 12. **Flask Extensions**

| Extension          | Purpose            |
| ------------------ | ------------------ |
| Flask-SQLAlchemy   | ORM                |
| Flask-Login        | Auth               |
| Flask-JWT-Extended | JWT Auth           |
| Flask-Migrate      | Alembic migrations |
| Flask-RESTful      | Class-based APIs   |
| Flask-CORS         | Cross-Origin setup |

---

### 13. **Deploying Flask**

* Via `gunicorn`, `uWSGI`, or Docker

```bash
gunicorn app:app
```

* Nginx can be used as a reverse proxy.

---

### 14. **Testing**

```python
client = app.test_client()
response = client.get('/')
assert response.status_code == 200
```

---

### 15. **Interview Questions**

* How does Flask handle requests internally?
* Explain Flask vs Django.
* How would you structure a large Flask app?
* What is WSGI and why is it needed?
* How do you handle user sessions or cookies?
* What is the purpose of Blueprints?

---
