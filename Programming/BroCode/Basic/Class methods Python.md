---
Created: 2025-06-05T07:05
tags:
  - OOP
---
Class methods = Allow operations related to the class itself  
Take (cls) as the first parameter, which represents the class itself.

```Python
"""
wala lang to hehe nakita ko lang sa shorts
from functools import lru_cache

@lru_cache
def fib(n:int):
    if n <= 1:
        return n
    else:
        return fib( n - 1 ) + fib( n - 2)
    
for i in range(0, 100):
    print(f'{i} : {fib(i)}')
"""
"""
as test for github
"""

class Student:

    count_students = 0

    total_gpa = 0

    def __init__(self, name, gpa):
        self.name = name
        self.gpa = gpa
        Student.count_students += 1
        Student.total_gpa += gpa


    def get_infp(self):
        return f"{self.name} {self.gpa}"

    @classmethod
    def get_count(cls):
        return f"Total number of students is {cls.count_students}"
    
    @classmethod
    def get_ave_gpa(cls):
        if cls.count_students != 0:
            return f"Average GPA : {cls.total_gpa / cls.count_students:.2d}"
        else:
            return 0
    

    
student1 = Student("Acob", 3.2)
student2 = Student("Goco", 2.5)
student3 = Student("Andy", 4.0)

print(Student.get_count())
print(Student.get_ave_gpa())
```