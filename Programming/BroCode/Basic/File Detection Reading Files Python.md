---
Created: 2025-06-05T07:12
tags:
  - OOP
---
```Python
import json
import csv

file_path_txt = "C:\\Users\\Cred\\Documents\\Coding\\Python\\OOP\\file_detection_TheFloder\\output number 2.txt"
file_path_json = "C:\\Users\\Cred\\Documents\\Coding\\Python\\OOP\\file_detection_TheFloder\\output number 3 the json.json"
file_path_csv = "C:\\Users\\Cred\\Documents\\Coding\\Python\\OOP\\file_detection_TheFloder\\output number 4 the csv.csv"

"""
try:
    with open(file_path_txt, "r") as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("File is not found")
except PermissionError:
    print("You do not have permission to read that file")
except json.decoder.JSONDecodeError:
    print("Error decoding json, it might not be json")
"""

"""
try:
    with open(file_path_json, "r") as file:
        content = json.load(file)
        print(content)
        print(content["name"])
        print(content["age"])
        print(content["position"])

except FileNotFoundError:
    print("File is not found")
except PermissionError:
    print("You do not have permission to read that file")
except json.decoder.JSONDecodeError:
    print("Error decoding json, it might not be json")
"""


try:
    with open(file_path_csv, "r") as file:
        content = csv.reader(file)
        for line in content:
            print(line)
            print(line[0])
            print(line[1])
            print(line[2])
            print()

except FileNotFoundError:
    print("File is not found")
except PermissionError:
    print("You do not have permission to read that file")
except json.decoder.JSONDecodeError:
    print("Error decoding json, it might not be json")
```