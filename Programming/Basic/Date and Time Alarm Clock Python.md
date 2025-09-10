---
Created: 2025-06-05T07:06
tags:
  - OOP
---
```Python
import time
import datetime
import pygame

"""
the init in pygame
(frequency: int = 44100, size: int = -16, channels: int = 2, buffer: int = 512, devicename: str | None = None, allowedchanges: int = 5) -> None
"""

def set_alarm(alarm_time):
    print(f"Alarm set for {alarm_time}")
    sound_file = "C:\\Users\\Cred\\Music\\Songs\\AKASAKIBunny GirlLyric Video.mp3"
    is_runnig = True

    while is_runnig:
        current_time = datetime.datetime.now().strftime("%H:%M:%S")
        print(current_time)

        if current_time == alarm_time:
            print("WAKE UP!!!")
            pygame.mixer.init()
            pygame.mixer.music.load(sound_file)
            pygame.mixer.music.play()

            while pygame.mixer.music.get_busy():
                time.sleep(1)

            is_runnig = False

        time.sleep(1)
    

if __name__ == '__main__':
    
    alarm_time = input("Enter the alarm time : (HH:MM:SS) : ")
    set_alarm(alarm_time )
```