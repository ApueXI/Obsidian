---
Created: 2025-07-18T18:12
---
## ✅ 1. Basic Usage

```Python
import logging

logging.debug("Debug message")     # Detailed info for debugging
logging.info("Info message")       # General info
logging.warning("Warning message") # Non-critical issue
logging.error("Error message")     # Something went wrong
logging.critical("Critical!")      # Serious error, program may stop
```

Default logging level = `WARNING` (so `DEBUG` & `INFO` won’t show unless configured).

---

## ✅ 2. Logging Levels

|Level|Numeric Value|Usage|
|---|---|---|
|`logging.DEBUG`|10|Detailed diagnostic info|
|`logging.INFO`|20|Normal runtime info|
|`logging.WARNING`|30|Something unexpected but not fatal|
|`logging.ERROR`|40|Error, functionality affected|
|`logging.CRITICAL`|50|Serious error, program may not continue|

---

## ✅ 3. Changing the Logging Level

```Python
logging.basicConfig(level=logging.DEBUG)
```

This will allow **DEBUG and above** to appear.

---

## ✅ 4. Custom Logging Format

```Python
logging.basicConfig(
    level=logging.DEBUG,
    format="%(asctime)s - %(name)s - %(levelname)s - %(message)s",
    datefmt="%Y-%m-%d %H:%M:%S"
)
```

**Common format specifiers:**

- `%(asctime)s` → Time
- `%(levelname)s` → Level name
- `%(name)s` → Logger name
- `%(message)s` → The log message
- `%(filename)s` → File name
- `%(lineno)d` → Line number

---

## ✅ 5. Logging to a File

```Python
logging.basicConfig(
    filename="app.log",
    filemode="a",  # append (default) | "w" overwrite
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)
```

---

## ✅ 6. Creating a Custom Logger

```Python
logger = logging.getLogger("my_app")
logger.setLevel(logging.DEBUG)

# Console Handler
console_handler = logging.StreamHandler()
console_handler.setLevel(logging.WARNING)

# File Handler
file_handler = logging.FileHandler("my_app.log")
file_handler.setLevel(logging.DEBUG)

# Formatter
formatter = logging.Formatter("%(name)s - %(levelname)s - %(message)s")
console_handler.setFormatter(formatter)
file_handler.setFormatter(formatter)

# Add handlers
logger.addHandler(console_handler)
logger.addHandler(file_handler)

logger.debug("Debug message")
logger.warning("Warning message")
```

---

## ✅ 7. Rotating Logs

Useful to prevent huge log files.

```Python
from logging.handlers import RotatingFileHandler

handler = RotatingFileHandler(
    "app.log", maxBytes=1000000, backupCount=3
)
logger = logging.getLogger("rotating_logger")
logger.addHandler(handler)
```

Or time-based rotation:

```Python
from logging.handlers import TimedRotatingFileHandler

handler = TimedRotatingFileHandler(
    "app.log", when="midnight", interval=1, backupCount=7
)
```

---

## ✅ 8. Exception Logging

```Python
try:
    1 / 0
except ZeroDivisionError:
    logging.exception("An exception occurred!")
```

`logging.exception()` automatically includes traceback info.

---

## ✅ 9. Disable Logging

```Python
logging.disable(logging.CRITICAL)  # disables all logs <= CRITICAL
```

---

## ✅ 10. Best Practices

✔ Always use `logging` instead of `print()` in production

✔ Use `__name__` for logger names (`logging.getLogger(__name__)`)

✔ Separate log config in a dedicated module/file for larger apps

✔ Use **different handlers** for console vs file logs

✔ Consider `RotatingFileHandler` or external log management