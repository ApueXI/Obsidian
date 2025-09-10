---
Created: 2025-06-05T07:03
---
```Python
userName = input("Enter a valid user name : ")

if len(userName) > 12:
    print("Your user name cannot exceed 12 letters")
elif not userName.find(" ") == -1:
    print("User name must not contain any spaces")
elif not userName.isalpha():
    print("User name must not contain any digits")
else:
    print(f"Welcome {userName}")
```

Python