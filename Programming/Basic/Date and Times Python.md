---
Created: 2025-06-05T07:07
tags:
  - OOP
---
```Python
import datetime

# year, month, day
date = datetime.date(2025, 1, 25)
date_today = datetime.date.today()

time = datetime.time(19, 31, 23)
time_now = datetime.datetime.now()

time_now = time_now.strftime("%H : %M : %S - %m/%d/%Y")

target_datetime = datetime.datetime(2030, 2, 2, 12, 30, 1)

current_datetime = datetime.datetime.now()

"""
print(date)
print(date_today)
print(time)
print(time_now)
"""

if target_datetime < current_datetime:
    print('Target date has passed')
else:
    print('Target date has not passed')
```