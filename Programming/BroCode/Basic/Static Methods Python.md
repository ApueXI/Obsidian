---
Created: 2025-06-05T07:23
tags:
  - OOP
---
Static methods = A method that belong to a class rather than any object from that class (instance) A #  
Usually used for general utility functions  
  
Instance methods = Best for operations on instances of the class (objects)  
\#Static methods = Best for utility functions that do not need access to class data  
from my undersatding, we use classmethod if ww want to use the calss variables

```Python
class Employee:

    is_hired = True

    def __init__(self, name, job_pos):
        self.name = name
        self.job_pos = job_pos

    def get_info(self):
        return f"{self.name} = {self.job_pos}"
    
    @staticmethod
    def is_valid_pos(job_pos):
        validpositions = ["Manager", "Cashier", "Janitor", "Cook"]
        return job_pos in validpositions

employee1 = Employee("Acob", "Manager")
employee2 = Employee("Goco", "Cashier")
employee3 = Employee("Andy", "Cook")

print(Employee.is_valid_pos("Cook"))
print(employee1.get_info())
print(employee2.get_info())
print(employee3.get_info())
```