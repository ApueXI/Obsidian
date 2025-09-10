---
Created: 2025-06-05T06:30
---
```Python
import math
"""
# My Version
myDictionary = {}
isUpdatingMyDictionary = True
listOfKeys = []
listOfValues = []
indexForKeys = 0
indexForValues = 0

while isUpdatingMyDictionary:
    keyForUpdating = input("Input a key : ")
    listOfKeys.append(keyForUpdating) 

    valueForUpdating = input("Input a Value : ")
    listOfValues.append(valueForUpdating)

    if not input("Do you want to add more key value pair? (y/n) : ").lower() == "y":
        isUpdatingMyDictionary = False

for dictioanryToUpdate in listOfKeys:
    myDictionary.update({listOfKeys[indexForKeys] : listOfValues[indexForValues]})
    indexForKeys+=1
    indexForValues+=1

for keyss, valuess in myDictionary.items():
    print(f"{keyss} : {valuess}")
"""

"""
Chatgpt Version .strip() removes the space in the beginning and end
myDictionary = {}
isUpdating = True

while isUpdating:
    key = input("Input a key: ")
    value = input("Input a value: ")
    myDictionary[key] = value  # simpler and direct

    more = input("Do you want to add more key-value pairs? (y/n): ").strip().lower()
    if more != "y":
        isUpdating = False

# Display the dictionary
print("\nFinal Dictionary:")
for k, v in myDictionary.items():
    print(f"{k} : {v}")
"""

myDictionary = {}
isUpdating = True
totalNgNagastosNgMgaTaongPumunta = 0
numberToLimit = 1
mgaTaoSaRizalSubejct = 33
minusSaMgaDiPumunta = 0
mgaMiminusSaMgaPumunta = []

howManyPeeps = int(input("How many people are in the film today : "))

while isUpdating:
    key = input("Sino pumunta     : ")
    value = input("Magkano Nagastos : ")
    myDictionary[key] = value

    # if not input("Do you want to add more key-value pairs? (y/n): ").strip().lower() == "y":
    #     isUpdating = False

    if howManyPeeps <= numberToLimit:
        isUpdating = False
    
    numberToLimit+=1

for gastos in myDictionary.values():
    gastos = int(gastos)
    totalNgNagastosNgMgaTaongPumunta+=gastos

cashBackOne = (totalNgNagastosNgMgaTaongPumunta / mgaTaoSaRizalSubejct )/ 2
cashBackOne = math.ceil(cashBackOne)
cashbackOneToConfirm = totalNgNagastosNgMgaTaongPumunta - (howManyPeeps * cashBackOne)

for valuess in myDictionary.values():
    valuess = int(valuess)
    valuess -= cashBackOne
    mgaMiminusSaMgaPumunta.append(valuess)
    minusSaMgaDiPumunta+=valuess
    
toCalculateMgaGagastusinNgMgaDipumunta = minusSaMgaDiPumunta / (mgaTaoSaRizalSubejct - howManyPeeps)
toCalculateMgaGagastusinNgMgaDipumunta = math.ceil(toCalculateMgaGagastusinNgMgaDipumunta)

print("-------------------Cash Back-------------------")
toIndexTheminusSaMgaDiPupunta = 0
for keys in myDictionary.keys():
    print(f"{keys} : {mgaMiminusSaMgaPumunta[toIndexTheminusSaMgaDiPupunta]}")
    toIndexTheminusSaMgaDiPupunta+=1

print(f"\nTotal ng magastos ng mga Pumunta : {totalNgNagastosNgMgaTaongPumunta}\n")
print(f"Minus sa mga pumunta : {cashBackOne}\n")
print(f"Total ng cashback para i minus sa total : {minusSaMgaDiPumunta}\n")
print(f"To confirm kung tama : {cashbackOneToConfirm}\n")
print(f"Mga aambagan ng mga di pumumnta : {toCalculateMgaGagastusinNgMgaDipumunta}")
```