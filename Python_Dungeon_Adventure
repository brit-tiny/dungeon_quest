import random

# Step 1: Player Setup
name = input("Ho there, goodly Sir/Madam...Smadam/Mir? Doth thee have a name: ")
health = 10
inventory = []

# Step 2: Treasure Dictionary
treasures = {
    "Coconut Halves": 10,
    "Shrubbery": 5,
    "Sir Bedevere's Scales": 50,
    "Holy Hand Grenade of Antioch": 100,
    "The Holy Grail": 200,
    "Book of Armaments": 75,
    "Excalibur": 150,
    "African Swallow": 25,
    "European Swallow": 25,
    "Lovely Filth": 1,
    "Golden Chalice": 100,
    "Ancient Coin": 50,
    "Shield of Antioch": 80,
    "Chastity Belt": 30,
    "Correct Answer": 10,
    "Black Knight's Leg": 15,
    "Black Knight's Arm": 15
}

traps = [
    {"name": "The Killer Rabbit of Caerbannog", "damage": 2, "counters": ["Holy Hand Grenade"]},
    {"name": "The Bridgekeeper’s Questions", "damage": 2, "counters": ["Correct Answer"]},
    {"name": "The Knights Who Say Ni!", "damage": 2, "counters": ["Shrubbery"]},
    {"name": "The Castle Anthrax Distraction", "damage": 2, "counters": ["Chastity Belt"]},
    {"name": "Flying Cow Ambush", "damage": 2, "counters": ["Shield of Antioch"]},
    {"name": "Dragon of Andor", "damage": 2, "counters": ["Holy Hand Grenade"]},
    {"name": "Dennis Galahad", "damage": 2, "counters": ["Lovely Filth"]}
]

room_names = [
    "The Castle of Aaargh",
    "Camalot",
    "The Bridge of Death",
    "The Chamber of Caerbannog",
    "The Castle Anthrax"
]
# Step 3: Game Loop - Moving through 5 rooms
for room in range(5):  # loop from 0 to 4
    room_name = room_names[room]
    print(f"\n--- Room {room + 1}: {room_name} ---")

    while True:
        print("\nChoose your action:")
        print("1. Search for treasure")
        print("2. Move to next room")
        print("3. Check health and inventory")
        print("4. Quit the game")
        choice = input("Enter your choice (1-4): ")

        if choice == "1":
            print("You chose to search for treasure...")
            outcome = random.choice(["treasure", "trap"])
            if outcome == "treasure":
                found = random.choice(list(treasures.keys()))
                inventory.append(found)
                print(f"You found {found}!")
                print(f"It is worth {treasures[found]} gold!")
            else:
                health -= 2
                trap = random.choice(traps)
                print(f"Trap triggered: {trap['name']}")
                
                has_counter = any(item in inventory for item in trap['counters'])

                if has_counter:
                    matching_item = next(item for item in trap['counters'] if item in inventory)
                    print(f"You used {matching_item} to avoid the trap!")
                else:
                    health -= trap['damage']
                    print(f"You take {trap['damage']} damage! You lack any of: {', '.join(trap['counters'])}")
        elif choice == "2":
            print("You move cautiously to the next room.")
            break
        elif choice == "3":
            print(f"Health: {health}")
            print("Inventory:", ", ".join(inventory) if inventory else "Empty")
        elif choice == "4":
            print("You chose to quit the adventure.")
            room = 5  # end the outer loop early
            break
        else:
            print("Invalid choice. Please select 1, 2, 3, or 4.")

        # Step 5: Check health
        if health <= 0:
            print("Your health has dropped to 0. Game Over!")
            break

    if health <= 0 or choice == "4":
        break

# Step 6: End of Game Summary
total_value = sum(treasures[item] for item in inventory)
print("\n--- Game Summary ---")
print(f"Adventurer: {name}")
print(f"Final Health: {health}")
print("Inventory:", ", ".join(inventory) if inventory else "Empty")
print(f"Total Treasure Value: {total_value} gold")
