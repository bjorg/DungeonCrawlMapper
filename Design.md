# Dungeon Crawl Mapper - Design Notes

## Node Types

* INTERSECTION: go left, straight, or right
* BATTLE: battle an enemy, then continue to another room
* TRAP: exit the dungeon
* TREASURE: collect the treasure and exit the dungeon
* EXTRA BALL: light the extra ball insert and exit the dungeon
* STAIRS DOWN: go to the next dungeon level

## Possible Node Transitions

```mermaid
graph BT;

    %% Node Labels
    START((Start));
    INTERSECTION(Intersection);
    TREASURE(Treasure);
    TRAP(Trap);
    STAIRS(Stairs Down);
    BATTLE(Battle);
    EB(Extra Ball);
    EXIT((Exit));

    %% Node Connections
    START --> INTERSECTION;
    INTERSECTION --> INTERSECTION;
    INTERSECTION --> TREASURE;
    INTERSECTION --> TRAP;
    INTERSECTION --> STAIRS;
    INTERSECTION --> BATTLE;
    INTERSECTION --> EB;
    TREASURE --> EXIT;
    TRAP --> EXIT;
    STAIRS -- "+1" --> START;
    BATTLE --> INTERSECTION;
    EB --> EXIT;
```
