# DungeonGame
The world for our game consists of a dungeon, a network of tunnels and caves that are interconnected so that player can explore the entire world by traveling from 
cave to cave through the tunnels that connect them. 
![image](https://user-images.githubusercontent.com/70654057/190240163-f58b085e-1bed-48f7-a2a5-a147df9da193.png)
![Uploading image.png…]()
This example dungeon is represented by a 6 x 8 two-dimensional grid. Each location in the grid represents a location in the dungeon where a player can explore and can be connected to at most four (4) other locations: one to the north, one to the east, one to the south, and one to the west. Notice that in this dungeon locations "wrap" to the one on the other side of the grid. For example, moving to the north from row 0 (at the top) in the grid moves the player to the location in the same column in row 5 (at the bottom). A location can further be classified as tunnel (which has exactly 2 entrances) or a cave (which has 1, 3 or 4 entrances). In the image above, we are representing caves as circular spaces.

In many games, these dungeons are generated at random following some set of constraints resulting in a different network each time the game begins. While the details on algorithms for generating a dungeon for our game are given in Part 2 - Implementation, we consider that an implementation detail. We provide the constraints that should be used for the design process:

The dungeon should be able to be represented on a 2-D grid.
There should be a path from every cave in the dungeon to every other cave in the dungeon.
Each dungeon can be constructed with a degree of interconnectivity. We define an interconnectivity = 0 when there is exactly one path from every cave in the dungeon to every other cave in the dungeon. Increasing the degree of interconnectivity increases the number of paths between caves.
Not all dungeons "wrap" from one side to the other (as defined above).
One cave is randomly selected as the start and one cave is randomly selected to be the end. The path between the start and the end locations should be at least of length 5.
The model should create and support a player moving through the world. To do this, it should support operations that allow:

both wrapping and non-wrapping dungeons to be created with different degrees of interconnectivity
provide support for at least three types of treasure: diamonds, rubies, and sapphires
treasure to be added to a specified percentage of caves. For example, the client should be able to ask the model to add treasure to 20% of the caves and the model should add a random treasure to at least 20% of the caves in the dungeon. A cave can have more than one treasure.
a player to enter the dungeon at the start
provide a description of the player that, at a minimum, includes a description of what treasure the player has collected
provide a description of the player's location that at the minimum includes a description of treasure in the room and the possible moves (north, east, south, west) that the player can make from their current location
a player to move from their current location
a player to pick up treasure that is located in their same location
Otyughs (Links to an external site.) are extremely smelly creatures that lead solitary lives in the deep, dark places of the world like our dungeon.

There is always at least one Otyugh in the dungeon located at the specially designated end cave. The actual number is specified on the command line. There is never an Otyugh at the start.
Otyugh only occupy caves and are never found in tunnels. Their caves can also contain treasure or other items.
They can be detected by their smell. In general, the player can detect two levels of smell:
a less pungent smell can be detected when there is a single Otyugh 2 positions from the player's current location
detecting a more pungent smell either means that there is a single Otyugh 1 position from the player's current location or that there are multiple Otyughs within 2 positions from the player's current location
They are adapted to eat whatever organic material that they can find, but love it when fresh meat happens into the cave in which they dwell. This means that a player entering a cave with an Otyugh that has not been slayed will be killed and eaten (see next section on how to slay an Otyugh).
Slaying Monsters
To give our player the ability to slay the Otyugh, they will automatically be equipped with a bow that uses crooked arrows

Player starts with 3 crooked arrows but can find additional arrows in the dungeon with the same frequency as treasure. Arrows and treasure can be, but are not always, found together. Furthermore, arrows can be found in both caves and tunnels.
A player that has arrows, can attempt to slay an Otyugh by specifying a direction and distance in which to shoot their crooked arrow. Distance is defined as the number of caves (but not tunnels) that an arrow travels. Arrows travel freely down tunnels (even crooked ones) but only travel in a straight line through a cave. For example,
a tunnel that has exits to the west and south can have an arrow enter the tunnel from the west and exit the tunnel to the south, or vice-versa (this is the reason the arrow is called a crooked arrow)
a cave that has exits to the east, south, and west will allow an arrow to enter from the east and exit to the west, or vice-versa; but an arrow that enters from the south would be stopped since there is no exit to the north
Distances must be exact. For example, if you shoot an arrow a distance of 3 to the east and the Otyugh is at a distance of 2, you miss the Otyugh.
It takes 2 hits to kill an Otyugh. Players has a 50% chance of escaping if the Otyugh if they enter a cave of an injured Otyugh that has been hit by a single crooked arrow.
Winning
The player wins by reaching the end location.
The player loses by being eaten by an Otyugh.
The controller should implement a text-based adventure game as described above. Your controller should be able to:

Use the input from the user to
navigate the player through the dungeon.
pick up treasure and/or arrows if they are found in the same location as the player
shoot an arrow in a given direction
Output clues about the nearby caves and other relevant aspects of the current game state without dumping the dungeon map to the screen.
