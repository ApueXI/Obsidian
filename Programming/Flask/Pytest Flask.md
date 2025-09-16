```python
# conftest.py
import pytest
from myapp import create_app, db as _db

@pytest.fixture(scope="session")
def app():
    """Create and configure a new app instance for tests."""
    app = create_app("config.TestConfig")
    with app.app_context():
        yield app

@pytest.fixture(scope="session")
def db(app):
    """Create a new database for the tests."""
    _db.app = app
    _db.create_all()
    yield _db
    _db.drop_all()

@pytest.fixture(scope="function", autouse=True)
def session(db):
    """Create a new database session for a test."""
    connection = db.engine.connect()
    transaction = connection.begin()
    options = dict(bind=connection, binds={})
    session = db.create_scoped_session(options=options)

    db.session = session
    yield session

    transaction.rollback()
    connection.close()
    session.remove()
```


### **Imports**
```python
import pytest from myapp import create_app, db as _db
```
- `pytest` → The testing framework that provides the fixture system.
- `create_app` → A factory function that creates your Flask app (commonly used to allow multiple configurations).
- `db as _db` → The SQLAlchemy instance from your app, renamed `_db` to avoid naming conflicts in fixtures.
---

### **App fixture**
```python
@pytest.fixture(scope="session")
def app():
"""Create and configure a new app instance for tests."""
	app = create_app("config.TestConfig")
	with app.app_context():
		yield app
```

- `@pytest.fixture(scope="session")` → Tells pytest to **create this fixture once per test session**, not for every test function.
- `app = create_app("config.TestConfig")` → Creates a Flask app using a **test configuration** (like in-memory SQLite).
- `with app.app_context():` → Enters a Flask application context. Many Flask operations (like database queries) require an **app context**.
- `yield app` → Provides the app to tests. After the `yield`, pytest will clean up if needed (though here, no extra cleanup is done).

---

### **Database fixture**
```python
@pytest.fixture(scope="session")
def db(app):
"""Create a new database for the tests."""
	_db.app = app
	_db.create_all()
	yield _db
	_db.drop_all()
```

- `scope="session"` → Only runs once per testing session.
- `_db.app = app` → Links the Flask app to the SQLAlchemy instance.
- `_db.create_all()` → Creates all tables defined in your SQLAlchemy models **before running tests**.
- `yield _db` → Provides the database instance to your tests.
- `_db.drop_all()` → Cleans up all tables **after all tests in the session finish**.

Essentially, this sets up a **fresh database** for all tests and cleans it afterward.

---

### **Session fixture**
```python
@pytest.fixture(scope="function", autouse=True)
def session(db):
	"""Create a new database session for a test."""
	connection = db.engine.connect()
	transaction = connection.begin()
	options = dict(bind=connection, binds={})
	session = db.create_scoped_session(options=options)
	
	db.session = session
	yield session
	
	transaction.rollback()
	connection.close()
	session.remove()
```
- `scope="function"` → Runs **once per test function**, giving each test a **fresh transaction**.
- `autouse=True` → Automatically applies this fixture to every test function, so you don’t need to explicitly include it.

**Inside the fixture:**

1. `connection = db.engine.connect()` → Opens a **raw database connection**.
2. `transaction = connection.begin()` → Starts a **transaction**. All test operations happen inside this transaction.
3. `options = dict(bind=connection, binds={})` → Sets up the session to use this specific connection.
4. `session = db.create_scoped_session(options=options)` → Creates a **scoped session** tied to the transaction. Scoped sessions are safe to use across multiple functions.
5. `db.session = session` → Makes this session the **current session** for the app, so `Model.query` works inside tests.
6. `yield session` → Provides the session to the test function.

**After the test finishes:**

- `transaction.rollback()` → Rolls back all changes, so the database stays **clean** for the next test.
- `connection.close()` → Closes the connection.
- `session.remove()` → Removes the session from the scoped session registry.

---

✅ **Summary of the fixtures:**

|Fixture|Scope|Purpose|
|---|---|---|
|`app`|session|Provides a Flask app instance for testing.|
|`db`|session|Creates and drops tables in a test database.|
|`session`|function|Provides a fresh database session for each test; rolls back changes automatically.|

---

This setup ensures:

1. Tests are **isolated** (one test doesn’t affect another).
2. Database is **in-memory or test-only**.
3. You can run **CRUD tests safely** on models.

---

```python
import pytest
from flask_jwt_extended import create_refresh_token, decode_token
from myapp import db
from myapp.models import User, RefreshToken

@pytest.fixture
def test_user():
    user = User(email="test@example.com", password="hashedpassword")
    db.session.add(user)
    db.session.commit()
    yield user
    db.session.delete(user)
    db.session.commit()


@pytest.fixture
def refresh_token(test_user):
    token_str = create_refresh_token(identity=test_user.id)
    jti = decode_token(token_str)["jti"]
    token = RefreshToken(jti=jti, user_id=test_user.id, revoked=False)
    db.session.add(token)
    db.session.commit()
    return token_str, token


def test_logout_success(client, refresh_token):
    token_str, token = refresh_token

    # send refresh token as cookie
    response = client.post(
        "/logout",
        cookies={"refresh_token_cookie": token_str}  # default cookie name in flask_jwt_extended
    )

    assert response.status_code == 200
    assert response.json["success"] is True
    assert "Successfully logged out" in response.json["message"]

    db.session.refresh(token)
    assert token.revoked is True


def test_logout_token_not_found(client):
    fake_token = create_refresh_token(identity=9999)

    response = client.post(
        "/logout",
        cookies={"refresh_token_cookie": fake_token}
    )

    assert response.status_code == 404
    assert "you dont have a token" in response.json["message"]


def test_logout_already_revoked(client, refresh_token):
    token_str, token = refresh_token
    token.revoked = True
    db.session.commit()

    response = client.post(
        "/logout",
        cookies={"refresh_token_cookie": token_str}
    )

    assert response.status_code == 404
    assert "JWT has been revoked" in response.json["message"]

```