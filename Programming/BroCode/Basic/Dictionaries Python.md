---
Created: 2025-06-05T06:29
---
dictionary = a collection of {key:Value} paire  
prdered and changable. No duplicates

```Python

capitals = {"USA": "Washington DC",
            "India" : "New Delhi",
            "China" : "Beijing",
            "Russia" : "Moscow"}

# print(dir(capitals))
# print(help(capitals))

"""
# gets the value
print(capitals.get("India"))
"""

"""
if capitals.get("Russia"):
    print("That capital exist")
else:
    print("That capital does not exist")
"""

# inserts or updates new key value pair
capitals.update({"Gemany" : "Berlin", "USA" : "Detroit", "Japan" : "Korea"})
capitals.update({"Philippines": "Manila"})
capitals.update({"Malaysia": "Kuala Lumpur"})

# Deletes the value
capitals.pop("China")

# Remove the latest key value pair
capitals.popitem()

# clear the dictionary
# capitals.clear()

# return the "Keys" witihn the dictionaries
keysOfTheCapital = capitals.keys()

# return the  "Values" witihn the dictionaries
valuesOfTheCapitals = capitals.values()

# return the key value pair
itemsOfTheCapitals = capitals.items()

"""
print(valuesOfTheCapitals)
print(valuesOfTheCapitals)

for keyss in capitals.keys():
    print(keyss)
print()
for valuess in capitals.values():
    print(valuess)
"""

"""
print(itemsOfTheCapitals)

for keyssss, valuesss in capitals.items():
    print(f"{keyssss} : {valuesss}")
print()
for items in capitals.items():
    print(items)
"""

# for values in capitals.values():
#     print(values)
```