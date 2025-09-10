---
Created: 2025-08-23T15:51
---
## 🔐 1. **Authentication & Authorization**

### ✅ Use `Flask-Login`

- Handles user session management (login, logout, session persistence).

```Bash
pip install flask-login

```

**Example:**

```Python
from flask import Flask, render_template, redirect, url_for
from flask_login import LoginManager, login_user, login_required, logout_user, UserMixin

app = Flask(__name__)
app.secret_key = 'your-secret-key'

login_manager = LoginManager()
login_manager.init_app(app)

class User(UserMixin):
    def __init__(self, id):
        self.id = id

# Simulated database
users = {"admin": {"password": "1234"}}

@login_manager.user_loader
def load_user(user_id):
    return User(user_id)

@app.route("/login", methods=["GET", "POST"])
def login():
    if request.method == "POST":
        username = request.form["username"]
        password = request.form["password"]
        if username in users and users[username]["password"] == password:
            user = User(username)
            login_user(user)
            return redirect(url_for("dashboard"))
    return render_template("login.html")

@app.route("/dashboard")
@login_required
def dashboard():
    return "Secure Dashboard"

@app.route("/logout")
@login_required
def logout():
    logout_user()
    return redirect(url_for("login"))

```

---

## 🧂 2. **Password Hashing**

### ✅ Use `Werkzeug.security`

```Python
from werkzeug.security import generate_password_hash, check_password_hash

hashed = generate_password_hash("mypassword")
is_valid = check_password_hash(hashed, "mypassword")

```

Never store plaintext passwords.

---

## 🛡 3. **CSRF Protection**

### ✅ Use `Flask-WTF` or `itsdangerous`

```Bash
pip install flask-wtf

```

**Setup:**

```Python
from flask_wtf import FlaskForm
from wtforms import StringField
from wtforms.validators import DataRequired

app.config['SECRET_KEY'] = 'supersecret'

```

**Template:**

```HTML
<form method="POST">
  {{ form.hidden_tag() }}
  {{ form.name.label }} {{ form.name() }}
  <input type="submit">
</form>

```

---

## 🔒 4. **HTTPS Only**

Force HTTPS to prevent data sniffing.

```Python
from flask_talisman import Talisman
Talisman(app)

```

```Bash
pip install flask-talisman

```

---

## 🧼 5. **Input Validation & Sanitization**

### ✅ Use `WTForms` or manual validation

- Sanitize all input.
- Avoid eval(), exec(), os.system() on user input.

---

## 🚫 6. **Prevent XSS (Cross-Site Scripting)**

- Flask's Jinja2 auto-escapes variables.
- Avoid using `|safe` unless necessary.
- Use `flask_talisman` to set security headers:

```Python
Talisman(app, content_security_policy=None)

```

---

## 🚧 7. **Prevent SQL Injection**

- Always use **ORMs** like SQLAlchemy or parameterized queries.

```Python
user = db.session.execute(
    text("SELECT * FROM users WHERE username=:username"),
    {"username": username}
)

```

---

## 🧱 8. **Security Headers with Flask-Talisman**

```Python
from flask_talisman import Talisman
Talisman(app)  # Adds CSP, HSTS, X-Frame-Options, etc.

```

---

## 🔍 9. **Session Security**

```Python
app.config.update(
    SESSION_COOKIE_SECURE=True,
    SESSION_COOKIE_HTTPONLY=True,
    SESSION_COOKIE_SAMESITE='Lax',
)

```

---

## 🔁 10. **Rate Limiting (to prevent brute-force)**

```Bash
pip install flask-limiter

```

```Python
from flask_limiter import Limiter
limiter = Limiter(app, key_func=get_remote_address)

@app.route("/login")
@limiter.limit("5 per minute")
def login():
    ...

```

---

## 📋 Summary Table

|Security Feature|Tool / Library|Notes|
|---|---|---|
|Authentication|Flask-Login|Manage sessions|
|Password Hashing|werkzeug.security|Never store plain passwords|
|CSRF Protection|Flask-WTF|Use `form.hidden_tag()`|
|HTTPS Enforcement|Flask-Talisman|Forces HTTPS, HSTS|
|Input Validation|WTForms|Clean & validate user input|
|SQL Injection Protection|SQLAlchemy, text()|Use parameterized queries|
|XSS Protection|Jinja2 autoescaping|Avoid using `|
|Rate Limiting|Flask-Limiter|Throttle abuse|
|Session Hardening|Flask configs|Set cookie flags|
|Secure Headers|Flask-Talisman|Set CSP, XFO, HSTS|

---

## 💡 Real-World Example Scenario

Let’s say you're building an **admin panel**. To secure it:

1. **Login page** uses Flask-Login with password hashed by Werkzeug.
2. **Login form** uses Flask-WTF to auto-handle CSRF.
3. Routes like `/admin` are decorated with `@login_required`.
4. SQL queries use SQLAlchemy or parameterized input to prevent injection.
5. Flask-Talisman enforces HTTPS and sets browser headers.
6. Session cookies are configured as HTTP-only, secure, and SameSite.
7. Login is rate-limited to 5 tries per minute.