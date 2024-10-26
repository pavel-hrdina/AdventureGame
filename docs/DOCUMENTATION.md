# Documentation for the project

This is the documentation for the project. It contains models.
Story details and other information about the project, like
the game controls and available options and outcomes.

# Table of Contents

Most of the links are not working, they are placeholders for now
as I will add documentation for the project, they will become
relevant.

## Working links or in progress

- [Project Progress](#project-progress)
- [Diagrams](#diagrams)
    - [Activity Diagram](#activity-diagram)
    - [State Diagram](#state-diagram)
    - [Class Diagram](#class-diagram)
    - [Flowchart Diagram](#flowchart-diagram)
- [Story](#story)
    - [Expanded Player Commands](#expanded-player-commands)
    - [Exploration](#exploration)
    - [Quest Progression](#quest-progression)
    - [Enemy Interactions](#enemy-interactions)
    - [Ending Openly on the First Floor](#ending-openly-on-the-first-floor)
    - [Conclusion](#conclusion)

## Inactive links

- [CI/CD Pipeline](#ci-cd-pipeline)a
- [Testing](#testing)
- [Game Design](#game-design)
    - [Map](#map)
- [Game Mechanics](#game-mechanics)
    - [Control Commands](#control-commands)
    - [Options](#options)
    - [Items](#items)
    - [Entities](#entities)
    - [Actions](#actions)
    - [Combat](#combat)
    - [Inventory](#inventory)
- [Map](#map)
- [Entities](#entities)
- [Items](#items)

## Project Progress

A table with project progress measured as tasks.

| task                     | status      | date      | updated   |
|--------------------------|-------------|-----------|-----------|
| Create diagrams          | in review   | 9/23/2024 | 9/24/2024 |
| Write a simple story     | in progress | 9/26/2024 | 9/26/2024 |
| Implement game mechanics | not started | 9/26/2024 |           |
| Create the map           | not started | 9/26/2024 |           |

## Diagrams

### Activity Diagram

![Activity Diagram](./assets/activityDiagram.svg)

### State Diagram

The explore action will change the state to the explore state, the interact action will change the state to
the interact state, the look at inventory action will change the state to the inventory
state, and the quit action will change the state to the quit state. The interact state
has the following actions: talk, take, use, back, attack. The explore state has the following
actions: go somewhere, go back. The inventory state has the following actions: list.
The quit will force the game to end and the application to close.

![State diagram](./assets/stateDiagram.svg)

### Class Diagram

**Core Classes**

* `Game` - *Main controller managing game flow*
* `Entity` - *Base class for all living beings*
* `Player` - *Specialized entity controlled by user*
* `Item` - *Interactive objects in the game world*
* `Location` - *Areas in the game world*
* `Story` - *Manages narrative and progression*
* `Action` - *Possible activities in game*
* `GameState` - *Tracks game progress and state*

**Attributes by Class**

* `Game`
    * *player*: Main player entity
    * *story*: Current story
    * *currentState*: Active game state
    * *isRunning*: Game activity status

* `Entity`
    * *name*: Entity identifier
    * *health*: Current health points
    * *maxHealth*: Maximum possible health
    * *currentLocation*: Current position
    * *isActive*: Activity status

* `Player` (extends Entity)
    * *inventory*: Carried items
    * *maxInventorySize*: Inventory capacity limit
    * *(inherits Entity attributes)*

* `Item`
    * *name*: Item identifier
    * *description*: Item details
    * *type*: ItemType value
    * *isCollectable*: Pickup status
    * *isUsable*: Usage status
    * *currentLocation*: Item position

* `Location`
    * *name*: Location identifier
    * *description*: Location details
    * *entities*: Present entities
    * *items*: Present items
    * *connectedLocations*: Linked locations
    * *isLocked*: Access status
    * *requiredKey*: Key item for unlocking

* `Story`
    * *title*: Story name
    * *introduction*: Opening narrative
    * *storyParts*: Story segments
    * *locations*: Available areas
    * *entities*: Present entities
    * *items*: Available items
    * *dialogues*: Conversation map
    * *availableActions*: Possible actions
    * *endings*: Possible conclusions
    * *currentPartIndex*: Story progress

* `Action`
    * *name*: Action identifier
    * *description*: Action details
    * *type*: ActionType value
    * *outcome*: Result description
    * *requirements*: Required conditions
    * *source*: Acting entity
    * *target*: Target entity
    * *itemUsed*: Required item

* `GameState`
    * *name*: State identifier
    * *description*: State description
    * *availableActions*: Current actions
    * *currentPart*: Active story segment
    * *flags*: State condition map

**Enumerations**

* `ItemType`
    * *KEY*: For unlocking
    * *WEAPON*: For combat
    * *CONSUMABLE*: Single-use
    * *QUEST_ITEM*: Story-related

* `ActionType`
    * *MOVEMENT*: Location changes
    * *INTERACTION*: Entity/object interaction
    * *USE_ITEM*: Item usage
    * *DIALOGUE*: Conversations
    * *COMBAT*: Fighting actions

**Key Methods by Class**

* `Game`
    * *initializeGame()*: Start setup
    * *processAction()*: Handle actions
    * *updateGameState()*: Update state
    * *endGame()*: Conclude game

* `Entity`
    * *move()*: Change location
    * *interact()*: Entity interaction
    * *getStatus()*: Status check
    * *takeDamage()*: Process damage
    * *heal()*: Recover health
    * *setLocation()*: Update position

* `Player`
    * *addItem()*: Add to inventory
    * *removeItem()*: Remove from inventory
    * *useItem()*: Use item
    * *getInventoryStatus()*: Check inventory
    * *canCarryItem()*: Check capacity

* `Item`
    * *use()*: Use item
    * *examine()*: Get details
    * *getInfo()*: Basic info
    * *setLocation()*: Update position
    * *onCollect()*: Collection behavior
    * *onUse()*: Usage behavior

* `Location`
    * *addEntity()*: Add entity
    * *removeEntity()*: Remove entity
    * *addItem()*: Add item
    * *removeItem()*: Remove item
    * *getAvailableItems()*: List items
    * *getConnectedLocations()*: List connections
    * *canEnter()*: Check access
    * *unlock()*: Process unlocking

* `Story`
    * *progressStory()*: Advance story
    * *getCurrentPart()*: Current segment
    * *getAvailableActions()*: List actions
    * *addStoryPart()*: Add segment
    * *checkTriggers()*: Check conditions
    * *getEnding()*: Get conclusion

* `Action`
    * *execute()*: Perform action
    * *checkRequirements()*: Validate conditions
    * *getDescription()*: Action details
    * *isAvailable()*: Check availability

* `GameState`
    * *updateState()*: Update state
    * *getAvailableActions()*: List actions
    * *getCurrentStatus()*: Get status
    * *setFlag()*: Set condition
    * *checkFlag()*: Check condition

**Key Relationships**

* Game contains one Player, Story, and GameState
* Player extends Entity
* Location contains multiple Entities and Items
* Locations connect to other Locations
* Story contains multiple Locations and Actions
* GameState tracks multiple Actions
* Items have one ItemType
* Actions have one ActionType
* Player carries multiple Items
* Entities and Items are in one Location

![Class Diagram](./assets/classDiagram.svg)

- [ ] All classes should implement appropriate error handling for invalid operations
- [ ] State changes should be monitored using an observer pattern
- [ ] Each class should maintain single responsibility principle
- [ ] Proper access modifiers should be used to ensure encapsulation
- [ ] Critical operations should include validation
- [ ] Consider adding a save/load system for game state persistence
- [ ] Implement proper cleanup for unused resources
- [ ] Add logging for debugging
- [ ] Consider adding a quest/objective tracking system
- [ ] Plan for future extensibility of item and action types

### Flowchart Diagram

The user will first start the game, then a story introduction will be displayed.
The user wil be asked for input, and the game will respond accordingly. There
are 3 choices the user can make, explore, interact, look at inventory and quit.
This will make the main game loop.

The game will try to check for a specific string in the user input, if it finds
it, it will execute the corresponding action. If it doesn't find it, it will
display an error message and ask the user to try again.

- [ ] TODO: Add string checking for user input in the flowchart.

![Flowchart Diagram](./assets/flowchartDiagram.svg)

## Story

**Setting:** A dark, ancient dungeon hidden beneath the village you
have visited the day before, filled with twisting corridors, forgotten
secrets, and lurking dangers.

---

**Introduction:**

You awaken in a damp stone cell, the air heavy with the scent of moss and decay.
The faint glow of torchlight flickers in the distance, casting long shadows on the
cold stone walls. You have no memory of how you got here, but you know one thing: you must escape.
Whispers echo through the halls, warning of dangers and treasures hidden within the dungeon's depths.

---

**Your Adventure Begins:**

You are in a **cell** with a rusty iron door. The room is dimly lit, revealing
a rickety wooden bench and a pile of old bones in the corner.

**What would you like to do?**

---

### Expanded Player Commands:

- **...EXAMINE...**
  *The door is locked tight, but you notice a small keyhole. The hinges are
  rusted, and a faint light seeps through the
  cracks around the door.*

- **...LOOK...*
  *You notice a loose stone in the wall that could be moved.
  It might hide something. The bench is unstable, but it looks
  like it could be used to reach higher areas if necessary.*

- **...LISTEN TO...**
  *You press your ear against the cold stone wall. In the distance, you hear the clanking
  of chains and soft murmurs. They seem to be coming from somewhere deeper within the
  dungeon, mixed with the faint sound of water dripping.*

- ****
  *You push against the door, but it doesn’t budge. A loud clang echoes, startling you.
  It seems the dungeon is more alive than you thought.*

---

### Exploration:

After you escape the cell, you enter a **dimly lit corridor** that stretches
ahead and branches off in several directions. The air is musty, and the walls
are covered in ancient symbols that glow faintly, revealing a path forward.

1. **North:** The corridor continues, with the sounds of water dripping echoing
   and a strange shimmer on the walls.
2. **East:** You see a faint light coming from around the corner, accompanied by the sound of voices.
3. **West:** A wooden door, slightly ajar, creaks softly as you approach.
   It smells of damp earth and something else—something unsettling.
4. **South:** The corridor ends in a dead end, but you notice a small alcove
   with a flickering torch and a pile of bones.

**What would you like to do?**

---

### Quest Progression:

As you navigate the dungeon, you’ll encounter various characters, obstacles, and enemies:

- **Fellow Prisoners:**
  *You stumble upon a fellow prisoner named Arin. He’s been trapped here for days and is desperate for escape. He offers
  to share what he knows about the dungeon in exchange for your help.*

- **Enemies:**
  *As you explore, you come across a **Shadow Wraith**, a dark figure that drifts silently through the corridor. Its
  hollow eyes seem to peer into your very soul, and it blocks your path with an air of menace. To pass, you must either
  find a way to defeat it or evade its gaze.*

- **Ancient Relics:**
  *You find a dusty tome on a ledge, filled with notes on the dungeon’s history. It hints at a hidden treasure and a way
  to bypass traps using specific incantations.*

- **Finding the Key:**
  *Deep within the dungeon, you learn from Arin that a **Dungeon Keeper** holds the key to the exit. The Keeper is a
  fierce creature that prowls the depths, and you will need to either confront it or find another way to get the key.*

---

### Enemy Interactions:

1. **Encountering the Shadow Wraith:**

- **Combat Option:** You can choose to fight the Wraith using a makeshift weapon found in the corridor.
    - If you succeed, the Wraith dissipates into shadows, leaving behind a small **Key Fragment** that could be
      important later.
    - If you fail, the Wraith drains your energy, forcing you to retreat back into the cell.

- **Evasion Option:** You can try to sneak past it, using your surroundings to hide. If successful, you avoid conflict
  but feel an unsettling presence watching your every move.

2. **Confronting the Dungeon Keeper:**

- You find the Keeper in a larger chamber filled with treasure and bones. It’s a hulking figure, guarding the **key**
  that you need.
- **Combat Option:** If you choose to fight, you can use the knowledge from the tome to exploit its weaknesses.
- **Negotiation Option:** Alternatively, you can attempt to negotiate with it. Perhaps it values something more than
  just a fight—like a promise of freedom or a trade for an item.

---

### Ending Openly on the First Floor:

After exploring, you reach a **large chamber** on the first floor.
The room is filled with remnants of what seems to have been an ancient
gathering space, now overrun with moss and darkness. In the center, a
heavy stone door stands before you. The air is thick with tension, and
the whispers grow louder, now forming words you can almost comprehend.

You realize this is the exit, but the door is locked with a complex mechanism
that requires the **Dungeon Keeper’s key** to open.

**Choices before the door:**

- **Investigate the chamber for clues** (to unlock the door).
- **Attempt to force the door open** (if you have the key).
- **Listen carefully to the whispers** (which may offer guidance).
- **Consult Arin for assistance** (to combine your knowledge and resources).

---

### Conclusion:

Your journey through the dungeon has led you to the brink of freedom,
but the path ahead remains uncertain. The whispers linger, hinting at
both danger and opportunity. Will you find a way to escape, or will the
secrets of the dungeon consume you?

With Arin by your side and the encounters you’ve faced, the choices
you make could change the course of your fate. The choice is yours,
and your adventure is far from over. Step forward and decide your fate,
knowing that every action may echo in the depths of the dungeon.

If I have time, I will add more details to the story and create a more complex narrative.
For now, this is a simple story to so that I can focus on learning and implementing the
game mechanics.