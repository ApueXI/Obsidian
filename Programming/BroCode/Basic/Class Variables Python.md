---
Created: 2025-06-05T06:23
tags:
  - OOP
---
class variables = Shared among all instances of a class

Defined outside the constructor

Allow you to share data among all objects created from that class

```Python
class Student:

    # class variable, can be accessed by any object
    class_year = 2024
    num_students = 0

    def __init__(self, name, age):
        self.name = name
        self.age = age
        # the num_students increments because __init__ runz twice cuz of student1 and student2
        Student.num_students += 1

student1 = Student("Acob", 50)
student2 = Student("Goco", 33)
student3 = Student("Andy", 77)
# student4 = Student("Zam", 41)

"""
print(student1.name)
print(student1.age)
print(student1.class_year)
# you can tell the class_year is a class variable cuz it cen be accesse by Student
print(Student.class_year)
print(Student.num_students)
"""
print(f"My graduating class of {Student.class_year} has {Student.num_students} students")
print(student1.name)
print(student2.name)
print(student3.name)
```