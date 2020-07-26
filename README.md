# Parcel Pickup

A maze solving agent with some additional limitations built using the LWJGL library.
Limitations:

1. The agent represents a moving car - the simulation keeps track of its orientation and speed. It can move forward and reverse, but cannot transition directly between these states - it needs to stop first (forward->stopped->reversing). The agent can only make turns while reversing or moving forward.
2. The agent has limited visibility - it can only see up to 4 squares away from its position.
3. The agent needs to find and pick up a pre-determined number of packages before it can exit the maze
4. Some of the packages present in the maze are inaccessible (surrounded by walls on all sides)
5. The agent has a limited amount of fuel to complete the maze
6. The agent takes damage if it ever hits a wall.

The agent utilizes the A* path finding algorithm to navigate to its goal, and decides what its goal is based on the following strategies:

1. If the required amount of parcels was picked up or the remaining fuel is only just enough to leave the maze (better to leave with some packages than run out of fuel and not deliver any), then the agent navigates to the maze exit.
2. If the agent sees a parcel and can find a traversable path to it, it navigates towards it.
3. Otherwise the agent navigates in a direction which would allow it to uncover the greatest amount of previously unseen tiles.

Tiles already seen by the agent are stored in a hashmap.

Run settings, in particular the map and the car controller can be changed by un/commenting appropriate lines in the Driving.Properties file.

Built as the final project of the University of Melbourne SWEN30006: Software Modelling and Design class.

![Car Controller UML diagram](https://github.com/Zejjs/ParcelPickup/blob/master/Parcel%20Pickup%20-%20UML.png?raw=true)
