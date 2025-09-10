---
Created: 2025-06-05T07:17
tags:
  - OOP
---
```Python
import os

filePath = "OOP/file_detection_TheTest.txt"
filePath2 = "file_detection_TheTest.txt"

# can use double back slash or forward slash
filePath3 = "C:\\Users\\Cred\\Documents\\Coding\\Python\\OOP\\file_detection_TheTestTestTest.text"

filePath4 = "C:\\Users\\Cred\\Documents\\Coding\\Python\\OOP\\file_detection_TheFloder"

sound_file = "C:\\Users\\Cred\\Music\\Songs\\AKASAKIBunny GirlLyric Video.mp3"


if os.path.exists(sound_file):
    print(f"the location '{sound_file}' exist")

    if os.path.isfile(filePath4):
        print("That is a file")
    elif os.path.isdir(filePath4):
        print("That is a directory")
    


else:
    print(f"That location does not exist")
```