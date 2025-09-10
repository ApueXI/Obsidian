---
Created: 2025-06-05T06:25
---
```Python
collections = single "variable" used to store multiple values
List = [] Ordered abd Changable. Duplicates OK
Set - {} Unordered and Immutable. bud Add/Remove OK. No Duplicates
Tuple = () Ordered and Unchangable. Duplicates OK. Faster . iteratable
"""

"""
to use the the help(), type ctrl + ` to open the terminal, then type python then enter, 
then type the collection you have then type in a new line (shift + enter) the function like, help(collectionVariableName)
> Steps
open terminal (ctrl + `)
type in "python"
type the collection variable, like Prutas = {"Durian", "Rambutan", "Dragonfruit", "Starapple"}
type help{Prutas}
```

```Python
fruits = ["apple", "Mango", "Banana", "Coconut"]

# like help but without the description
# print(dir(fruits))
# mine doesnt work but it shows what you can do in the list with description
# print(help(fruits))

# List

# changes the value
fruits[0] = "Pineapple"

# adds an element to the end of the list
fruits.append("Kiwi")

# removes an specific string
fruits.remove("Kiwi")

# insert an element to a specific index
fruits.insert(0, "Kiwi")

# sorts alphabetically
fruits.sort()

# reverses the order of the list, it does not reveres it alphabetically
fruits.reverse()

# removes all the element
# fruits.clear()

# # You can use any string indexing method here
# print(fruits[::-1])

# counts the length of the lsit
print(len(fruits))

# finds if a string is in the list, returns a bool
print("Pineapple" in fruits)

# returns the index of a certain element
print(fruits.index("Kiwi"))

# Counts how many a certain element is repeated
print(fruits.count("Kiwi"))

print(fruits)

# Set
Prutas = {"Durian", "Rambutan", "Dragonfruit", "Starapple"}

# can use the same command as List
# cant use indexing since this is unordered

# print(dir(Prutas))
# help(Prutas)

# adds an element
Prutas.add("Lychee")

# Removes an Element
Prutas.remove("Lychee")

# Removes the first element, but since this is unordered it will be randomed
Prutas.pop()

print(Prutas)

# Tupple

theFruits = ("Mangosteen", "MiracleFruit", "Salak", "Sapodilla")

print(theFruits)

# only have count and index
# print(dir(theFruits))
# help(theFruits)

print(len(theFruits))
print("Mangosteen" in theFruits)
print(theFruits.index("Salak"))
print(theFruits.count("Salak"))
```