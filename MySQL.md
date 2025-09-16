
```SQL
CREATE USER 'flask_user'@'localhost' IDENTIFIED BY 'nein0226';
GRANT ALL PRIVILEGES ON flask_db.* TO 'flask_user'@'localhost';
FLUSH PRIVILEGES;
```