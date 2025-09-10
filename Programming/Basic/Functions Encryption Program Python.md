---
Created: 2025-06-05T06:41
---
```Python
import random
import string

# this or just print chars
chars = " " + string.punctuation + string.digits + string.ascii_letters
chars = list(chars)
key = chars.copy()

random.shuffle(key)

print(f"chars : {chars}")
print(f"key : {key}")

# Encrypt
plain_text = input("Enter a message to encrypt : ")
cypher_text = ""

for letter in plain_text:
    index = chars.index(letter)
    cypher_text += key[index]

print(f"Original Message : {plain_text}")
print(f"Encrypten Message : {cypher_text}")

# Decrypt
cypher_text = input("Enter a message to encrypt : ")
plain_text = ""

for letter in cypher_text:
    index = key.index(letter)
    plain_text += chars[index]

print(f"Encrypten Message : {cypher_text}")
print(f"Original Message : {plain_text}")
```