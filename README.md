# OpenSpiel bd_mines Levels
This repo contains levels formatted from the classic Boulder Dash game, for the [open_spiel](https://github.com/deepmind/open_spiel) `bd_mines` game.

## Level Format
The level data is formatted as a comma-separated string. The fist line should contain the number of columns, number of rows, the number of steps before time runs out, and the number of gems required.

The following lines represent the map elements. Each line represents a separate row. For each line, comma-separate each element ID, such that the number of items on each row matches the number of columns specified above. The number of rows should also match.

**Note:** Ensure that there is no trailing new-line at the end of the file.

## Element IDs
The following are the supported elements, along with their IDs. **Note:** Some IDs are not listed, as they are interal elements which represent special elements (falling objects, explosions, etc.)
- Rockford (Agent) -> 0
- Empty -> 1
- Dirt -> 2
- Boulder -> 3
- Diamond -> 5
- Exit Closed -> 7
- Firefly Up -> 10
- Firefly Left -> 11
- Firefly Down -> 12
- Firefly Right -> 13
- Butterfly Up -> 14
- Butterfly Left -> 15
- Butterfly Down -> 16
- Butterfly Right -> 17
- Brick Wall -> 18
- Steel Wall -> 19
- Magic Wall -> 20
- Amoeba -> 23

## Element Descriptions
A detailed explanation of each element is given below.
- Rockford (Agent): Rockford can move up, down, left, or right. As he moves through dirt, it is removed and left with an empty space. Rockford can be killed by falling objects, or enemies such as amoeba, fireflies, and butterflies.
- Empty: An empty space, allowing elements to move through.
- Dirt: Prevents objects from falling downwards.
- Boulder: Can fall down, and will explode when impacted on enemies or Rockford. Boulders can also roll off rounded objects. Boulders can be pushed horizontally by Rockford if there is an empty space on the other side.
- Diamond: Similar to boulders, except Rockford gains points when collected. Diamonds need to be collected to complete the level.
- Exit Closed: The end goal for Rockford. Must have diamonds collected before it opens.
- Fireflies: Can be oriented up, down, left, or right. Fireflies try to move clockwise. Will explode if a rock falls on it.
- Butterflies: Same as fireflies, but will try to move counter-clockwise. Will turn to diamonds if a rock falls on it
- Brick Wall: A rounded wall, which can be consumed if an explosion happens beside.
- Steel Wall: An indestructible wall.
- Magic Wall: Converts diamonds to rocks, and rocks to diamonds if active. Becomes active by dropping a rock through it. Will only remain active for a specified number of steps. There must be room beneath for items to fall through.
- Amoeba: Will grow into neighbouring cells, if empty or dirt. Amoebas have a random chance of growing, as well as the specified direction. If surrounded by elements such as rocks, the amoeba will turn to diamonds. If amoebas grow too large, they will turn to boulders.