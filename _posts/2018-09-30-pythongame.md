---
title: "Programming Project: Army of One"
date: 2018-09-30
tags: [python]
header:
    image: "images/pythontm.png"
excerpt: "First ever programming project, created in Python."
gallery:
  - url: /images/pythongame1.png
    image_path: images/pythongame1.png
    alt: "The title screen"
  - url: /images/pythongame2.png
    image_path: images/pythongame2.png
    alt: "Game in progress"
  - url: /images/pythongame3.png
    image_path: images/pythongame3.png
    alt: "Final boss fight"
  - url: /images/pythongame4.png
    image_path: images/pythongame4.png
    alt: "Victory screen"
---

This is the first large programming project I ever undertook in my studies,
it allowed me to include all the basic programming techniques I had learned from 
my first term as well as topics we hadn't covered like basic object oriented programming.

<h3>Classes:</h3>

```python

class Player(object):
    """The Player Character"""

    def __init__(self, name):
        self.name = name
        self.inventory = []
        self.weapon = weapons[0]
        self.armour = armours[0]
        self.hp = 200
        self.maxhp = 200
        self.attack = 10        
        self.heal = 50
        self.heal_count = 5
        self.magic_attack = 50
        self.magic_count = 5

    def __str__(self):
        return "\t{}\n\t************\n{}\n{}\n{}\n{}\n{}\n{}\n{}\n".format(self.name, self.inventory, self.weapon, self.armour, self.hp, self.attack, self.heal, self.heal_count)

    def is_alive(self):
        return self.hp > 0

```

<h3>Unpacking Textfiles To Create Class Objects:</h3>

```python

# Function to unpack the enemy text file and create Enemy class objects to append to a list.
def enemy_unpack(file):
    """Creating all enemies from a text file"""
    with open(file, "r") as f:
        enemies = []
        for line in f:
            line = line.strip()
            line = line.replace("/", "\n")
            line = line.split("*")

            name = line[0]
            hp = int(line[1])
            maxhp = int(line[2])
            attack = int(line[3])
            heal_count = int(line[4])
            heal = int(line[5])
            magic_count = int(line[6])
            magic_attack = int(line[7])

            enemy = Enemy(name, hp, maxhp, attack, heal_count, heal, magic_count, magic_attack)
            enemies.append(enemy)
        return enemies

```

<h3>Loading Information From Files To Create Rooms and Content:</h3>

```python
# The Room class.
class Room:
    """All Rooms in the game"""
    def __init__(self, name, description, items, enemy):
        self.name = name
        self.description = description
        self.items = [items]
        self.enemy = enemy

    def __str__(self):
        return "\t{}\n\t************\nDescription: {}\nItems: {}\nEnemy: {}".format(self.name, self.description, self.items, self.enemy)

# Unpacks the game room text file, formatting all the data within, utilising the format class function.
    def room_unpack(file):
        """Creating all objects from a text file"""
        with open(file, "r") as f:   
            rooms = []
            for line in f:
                line = line.strip()
                line = line.replace("/", "\n")
                line = line.split("*")
                name = line[0]
                description = line[1]
                items = format_class(line[2])
                enemy = format_class(line[3])

                room = Room(name, description, items, enemy)
                rooms.append(room)
            return rooms

```

<h3>Using Data Structures Like Dictionaries To Create Maps:</h3>

```python
    # Function to open the map file into a dictionary (adjacency list), utilises the format_vari function.
    def open_map(text):
        """To open a map from a text file"""
        world_map = {}
        for line in open(text,'r'):
                line2 = line.split()
                room = line2[0]
                room = format_vari(room)
                #print(room)
                room_loc = line2[1:]
                #print(room_loc)
                room_location = []
                for location in room_loc:
                    location = format_vari(location)
                    #print(location)
                    room_location.append(location)

                world_map[room]=room_location

        return world_map
```

{% include gallery caption="Various game screens and gameplay" %}

<a href="https://github.com/Sir-Benj/Python-First-Game">This</a> is a link to the GitHub repository for the project.

The project documentation can also be found <a href="https://github.com/Sir-Benj/Portfolio/blob/master/documentation/Python_Project_Documentation.docx">here</a>.