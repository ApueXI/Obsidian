---
Created: 2025-06-17T18:41
---
```Bash
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

  

```Bash
.\venv\Scripts\activate.ps1 or
venv\Scripts\activate
```

  

```Bash
pip3 install virtualenv
virtualenv venv
pip install -r requirements.txt
pip freeze > requirements.txt
```

  

```Bash
python
import secrets
secrets.token_hex()
```

  

---

  

```Python
with app.app_context():
db.create_all()
```

  

```Python
@app.teardown_appcontext
def shutdown_session(exception=None):
    db.session.remove()

return app
```

  

```Python
def create_database(app):
    db_path = Path(app.root_path) / DB_NAME
    if not db_path.exists():
        with app.app_context():
            db.create_all()
            logger.info("Database Created")
```