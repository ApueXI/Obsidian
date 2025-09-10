---
Created: 2025-06-05T07:20
tags:
  - OOP
---
multithreading = Used to perform multiple tasks concurrently (multitasking)  
Good for I/O bound tasks like reading files or fetching data from APIs  
threading.Thread(target=my_function)

```Python
import threading
import time

def walk_dog(fName):
    time.sleep(8)
    print(f"YOu finihsed walking {fName}")
    
def take_out_trask(trash, where):
    time.sleep(2)
    print(f"You took the trash {trash}, in the {where}")

def get_mail():
    time.sleep(4)
    print("YOu get mail")

chore1 = threading.Thread(target=walk_dog, args=("scooby",))
chore1.start()

chore2 = threading.Thread(target=take_out_trask, args=("Banana", "Dumpster"))
chore2.start()

chore3 = threading.Thread(target=get_mail)
chore3.start()

chore1.join()
chore2.join()
chore3.join()

print("All chores are complete")
```