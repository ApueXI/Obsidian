---
Created: 2025-06-05T07:23
tags:
  - OOP
---
```Python
import requests 

# getting 200 from response means its ok

base_url = "https://pokeapi.co/api/v2/"

def get_pokemon(name):
    url = F"{base_url}/pokemon/{name}"
    response = requests.get(url)

    if response.status_code == 200:
        print("Data Retreived")
        pokemon_data = response.json()
        return pokemon_data
    
    else:
        print(f"Failed to retreive data {response.status_code}")

pokomen_name = "typhlosion"
pokemon_info = get_pokemon(pokomen_name)

if pokemon_info:
    print(f"Name : {pokemon_info["name"].capitalize()}")
    print(f"ID : {pokemon_info["id"]}")
    print(f"Height : {pokemon_info["height"]}")
    print(f"Weight : {pokemon_info["weight"]}")
    for ability in pokemon_info["abilities"]:
        print(f"Abilities : {ability}")
    print(f"Base_experience : {pokemon_info["base_experience"]}")


# for info in pokemon_info:
#     print(pokemon_info[info])
"""
cries
forms
game_indices
height
held_items
id
is_default
location_area_encounters
moves
name
order
past_abilities
past_types
species
sprites
stats
types
weight
"""
```