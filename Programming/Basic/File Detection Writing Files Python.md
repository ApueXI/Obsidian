---
Created: 2025-06-05T07:16
tags:
  - OOP
---
```Python
# Python writing fiels (.text, .json, .csv)

import json
import csv

text_data = "i like pizza"

employees = ["Acob", "Goco", "Andy", "Zam"]

# json fi;e is a collection of key value pairs
employee_json = {
    "name" : "Acob",
    "age" : 30,
    "position" : "cook"
}

# csv = comma seperated value
employee_csv = [["Name", "Age", "Job"],
                ["Acob", 60 , "Cook"],
                ["Goco", 26, "Cashier"],
                ["Andy", 18, "Homeless"]]

file_path = "output.txt"
file_path2 = "C:\\Users\\Cred\\Documents\\Coding\\Python\\OOP\\file_detection_TheFloder\\output number 2.txt"
file_path_json = "C:\\Users\\Cred\\Documents\\Coding\\Python\\OOP\\file_detection_TheFloder\\output number 3 the json.json"
file_path_csv = "C:\\Users\\Cred\\Documents\\Coding\\Python\\OOP\\file_detection_TheFloder\\output number 4 the csv.csv"

"""
(file: FileDescriptorOrPath, mode: OpenTextMode = "r", buffering: int = -1, encoding: str | None = None, errors: str | None = None, newline: str 
                                                | None = None, closefd: bool = True, opener: _Opener | None = None) -> TextIOWrapper[_WrappedBuffer]
"""

"""
with is a statement used to wrap a block oc code to execute
with statement will also close the file of we are done with it
2nd arguemnt is the mode, 'w' is write, 
'x' will also write if the file does not exist, if it exist we will reveice an error
'a' to append a file
'r' is to read
open function returns a file object
can be set as key word arguemnts(kwargs) it its easy to read
use 'as' keyword to give it a name, kinf of like instantiate an object 
# Csv is like a excel spreadsheet

can use contatination   
file.write(text_data + "\n")
"""

"""
# text file
try:
    with open(file=file_path2, mode="w") as file:
        for employee in employees:
            file.write(employee + "\n")
        print(f"text file '{file_path2}' was created") 
except FileExistsError:
    print("File already exist")
"""


# json file
# can use kwarg as a argument, e.g. 'indeent=' here
try:
    with open(file=file_path_json, mode="w") as file:

        json.dump(employee_json, file, indent=4)

        print(f"json file '{file_path_json}' was created") 
except FileExistsError:
    print("File already exist")

"""
# Csv is like a excel spreadsheet
try:
    with open(file=file_path_csv, mode="w", newline="") as file:

        writer = csv.writer(file)

        for row in employee_csv:
            writer.writerow(row)

        print(f"csv file '{file_path_csv}' was created") 
except FileExistsError:
    print("File already exist")
    """
```