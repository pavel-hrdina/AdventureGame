# Documentation for the project

This is the documentation for the project. It contains models.
Story details and other information about the project, like 
the game controls and available options and outcomes.

## Project Progress

A table with project progress measured as tasks.

| task            | status      | date      | updated   |
|-----------------|-------------|-----------|-----------|
| Create diagrams | in progress | 9/23/2024 | 9/24/2024 |

## Diagrams

Diagrams for the project are:

- [Activity Diagram](#activity-diagram)
- [Class Diagram]()
- [State Diagram](#state-diagram)
- [Component Diagram]()
- [Deployment Diagram]()
- [Flowchart Diagram](#flowchart-diagram)


### Activity Diagram

![Activity Diagram](./assets/activityDiagram.svg)

### State Diagram

The explore action will  change the state to the explore state, the interact action will change the state to
the interact state, the look at inventory action will change the state to the inventory
state, and the quit action will change the state to the quit state. The interact state
has the following actions: talk, take, use, back, attack. The explore state has the following
actions: go somewhere, go back. The inventory state has the following actions: list. 
The quit will force the game to end and the application to close.

![State diagram](./assets/stateDiagram.svg)

### Flowchart Diagram

The user will first start the game, then a story introduction will be displayed.
The user wil be asked for input, and the game will respond accordingly. There
are 3 choices the user can make, explore, interact, look at inventory and quit.
This will make the main game loop.

![Flowchart Diagram](./assets/flowchartDiagram.svg)
