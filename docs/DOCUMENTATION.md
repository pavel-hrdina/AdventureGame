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

- [CI/CD Pipeline](#ci-cd-pipeline)
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

- `Game` - _Main controller managing game flow_
- `Entity` - _Base class for all living beings_
- `Player` - _Specialized entity controlled by user_
- `Item` - _Interactive objects in the game world_
- `Location` - _Areas in the game world_
- `Story` - _Manages narrative and progression_
- `Action` - _Possible activities in game_
- `GameState` - _Tracks game progress and state_

**Attributes by Class**

- `Game`

    - _player_: Main player entity
    - _story_: Current story
    - _currentState_: Active game state
    - _isRunning_: Game activity status

- `Entity`

    - _name_: Entity identifier
    - _health_: Current health points
    - _maxHealth_: Maximum possible health
    - _currentLocation_: Current position
    - _isActive_: Activity status

- `Player` (extends Entity)

    - _inventory_: Carried items
    - _maxInventorySize_: Inventory capacity limit
    - _(inherits Entity attributes)_

- `Item`

    - _name_: Item identifier
    - _description_: Item details
    - _type_: ItemType value
    - _isCollectable_: Pickup status
    - _isUsable_: Usage status
    - _currentLocation_: Item position

- `Location`

    - _name_: Location identifier
    - _description_: Location details
    - _entities_: Present entities
    - _items_: Present items
    - _connectedLocations_: Linked locations
    - _isLocked_: Access status
    - _requiredKey_: Key item for unlocking

- `Story`

    - _title_: Story name
    - _introduction_: Opening narrative
    - _storyParts_: Story segments
    - _locations_: Available areas
    - _entities_: Present entities
    - _items_: Available items
    - _dialogues_: Conversation map
    - _availableActions_: Possible actions
    - _endings_: Possible conclusions
    - _currentPartIndex_: Story progress

- `Action`

    - _name_: Action identifier
    - _description_: Action details
    - _type_: ActionType value
    - _outcome_: Result description
    - _requirements_: Required conditions
    - _source_: Acting entity
    - _target_: Target entity
    - _itemUsed_: Required item

- `GameState`
    - _name_: State identifier
    - _description_: State description
    - _availableActions_: Current actions
    - _currentPart_: Active story segment
    - _flags_: State condition map

**Enumerations**

- `ItemType`

    - _KEY_: For unlocking
    - _WEAPON_: For combat
    - _CONSUMABLE_: Single-use
    - _QUEST_ITEM_: Story-related

- `ActionType`
    - _MOVEMENT_: Location changes
    - _INTERACTION_: Entity/object interaction
    - _USE_ITEM_: Item usage
    - _DIALOGUE_: Conversations
    - _COMBAT_: Fighting actions

**Key Methods by Class**

- `Game`

    - _initializeGame()_: Start setup
    - _processAction()_: Handle actions
    - _updateGameState()_: Update state
    - _endGame()_: Conclude game

- `Entity`

    - _move()_: Change location
    - _interact()_: Entity interaction
    - _getStatus()_: Status check
    - _takeDamage()_: Process damage
    - _heal()_: Recover health
    - _setLocation()_: Update position

- `Player`

    - _addItem()_: Add to inventory
    - _removeItem()_: Remove from inventory
    - _useItem()_: Use item
    - _getInventoryStatus()_: Check inventory
    - _canCarryItem()_: Check capacity

- `Item`

    - _use()_: Use item
    - _examine()_: Get details
    - _getInfo()_: Basic info
    - _setLocation()_: Update position
    - _onCollect()_: Collection behavior
    - _onUse()_: Usage behavior

- `Location`

    - _addEntity()_: Add entity
    - _removeEntity()_: Remove entity
    - _addItem()_: Add item
    - _removeItem()_: Remove item
    - _getAvailableItems()_: List items
    - _getConnectedLocations()_: List connections
    - _canEnter()_: Check access
    - _unlock()_: Process unlocking

- `Story`

    - _progressStory()_: Advance story
    - _getCurrentPart()_: Current segment
    - _getAvailableActions()_: List actions
    - _addStoryPart()_: Add segment
    - _checkTriggers()_: Check conditions
    - _getEnding()_: Get conclusion

- `Action`

    - _execute()_: Perform action
    - _checkRequirements()_: Validate conditions
    - _getDescription()_: Action details
    - _isAvailable()_: Check availability

- `GameState`
    - _updateState()_: Update state
    - _getAvailableActions()_: List actions
    - _getCurrentStatus()_: Get status
    - _setFlag()_: Set condition
    - _checkFlag()_: Check condition

**Key Relationships**

- Game contains one Player, Story, and GameState
- Player extends Entity
- Location contains multiple Entities and Items
- Locations connect to other Locations
- Story contains multiple Locations and Actions
- GameState tracks multiple Actions
- Items have one ItemType
- Actions have one ActionType
- Player carries multiple Items
- Entities and Items are in one Location

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
cold stone walls. You have no memory of how you got here, but you know one
thing: you have come for something, yet you fail to remember, what happened? What brought you here?
The answers are lost in the darkness of your mind.

Whispers echo through the halls, warning of dangers and treasures hidden within the dungeon's depths.

---

**Your Adventure Begins:**

You are in a **cell** with a rusty iron door. The room is dimly lit, revealing
a rickety wooden bench and a pile of old bones in the corner.

**What would you like to do?**

---

### Expanded Player Commands:

- **...EXAMINE...**
  _The door is locked tight, but you notice a small keyhole. The hinges are
  rusted, and a faint light seeps through the
  cracks around the door._

- \*_...LOOK..._
  _You notice a loose stone in the wall that could be moved.
  It might hide something. The bench is unstable, but it looks
  like it could be used to reach higher areas if necessary._

- **...LISTEN TO...**
  _You press your ear against the cold stone wall. In the distance, you hear the clanking
  of chains and soft murmurs. They seem to be coming from somewhere deeper within the
  dungeon, mixed with the faint sound of water dripping._

- ***
  _You push against the door, but it doesn’t budge. A loud clang echoes, startling you.
  It seems the dungeon is more alive than you thought._

Will add more options when the mechanics are designed.

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

## **What would you like to do?**

### Quest Progression:

As you navigate the dungeon, you’ll encounter various characters, obstacles, and enemies:

- **Fellow Prisoners:**
  _You stumble upon a fellow prisoner named Arin. He’s been trapped here for
  days and is desperate for escape. He offers to share what he knows about the
  dungeon in exchange for your help._

- **Enemies:**
  _As you explore, you come across a **Shadow Wraith**, a dark figure that drifts
  silently through the corridor. Its hollow eyes seem to peer into your very soul, and
  it blocks your path with an air of menace. To pass, you must either find a way to defeat
  it or evade its gaze._

- **Ancient Relics:**
  _You find a dusty tome on a ledge, filled with notes on the dungeon’s history.
  It hints at a hidden treasure and a way to bypass traps using specific incantations._

- **Finding the Key:**
  _Deep within the dungeon, you learn from Arin that a **Dungeon Keeper** holds the key to the exit. The Keeper is a
  fierce creature that prowls the depths, and you will need to either confront it or find another way to get the key._

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

Every encounter will have consequences, shaping the story and your character’s journey. If
you fail to defeat an enemy, you may lose health or be forced to retreat, altering your path
through the dungeon, you may even lose the game.

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