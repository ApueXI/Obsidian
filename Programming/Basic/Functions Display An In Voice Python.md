---
Created: 2025-06-05T06:36
---
```Python
def display_Invoice(username, amount, due_date):
    print(f'Hello {username}')
    print(f'Your bill of ${amount:.02f} is due {due_date}')

display_Invoice("BroCode", 43.56, 'First of January')
```