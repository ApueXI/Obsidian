---
Created: 2025-06-05T07:18
tags:
  - OOP
---
Magic methods = Dunder methods (double underscore) _init_, _str_, _eq_  
They are automatically called by many of Python's built-in operations.  
They allow developers to define or customize the behavior of objects

```Python
class Book:

    def __init__(self, title, author, num_pages):
        self.title = title
        self.author =author
        self.num_pages = num_pages

    def __str__(self):
        return f"'{self.title}' by {self.author}"
    
    def __eq__(self, other):
        return self.title == other.title and self.author == other.author
    
    def __lt__(self, other):
        return self.num_pages < other.num_pages
    
    def __gt__(self, other):
        return self.num_pages > other.num_pages
    
    def __add__(self, other):
        return f"{self.num_pages + other.num_pages} pages" 
    
    def __contains__(self, keyword):
        return keyword in self.title or keyword in self.author
    
    def __getitem__(self, key):
        if key == "title":
            return self.title
        elif key == 'Author':
            return self.author
        elif key == 'num_pages':
            return self.num_pages
        else:
            return f"Key {key} was not found"
        
    
book1 = Book("The Hobbit", "J.R.R. Tolkien", 310)
book2 = Book("Harry Potter and the Philosopher Stone", "J.K. Rowling", 223)
book3 = Book("The Lion, the witch and the wardrobe", "C.S Lewis", 172)
book4 = Book("The Lion, the witch and the wardrobe", "C.S Lewis", 256)

# def __str__
print("\ndef __str__")
print(book1)
print(book2)
print(book3)

# def __eq__
print("\ndef __eq__")
print(book3 == book4)

# def __lt__
print("\ndef __lt__")
print(book1 < book2)

# def __gt__
print("\ndef __gt__")
print(book1 > book3)

# def __add__
print("\ndef __add__")
print(book1 + book4)

# def __contains__
print("\ndef __contains__")
print("Rowling" in book2)

# def __getitem__
print("\ndef __getitem__")
print(book1['title'])
print(book1['Author'])
print(book1['num_pages'])
```