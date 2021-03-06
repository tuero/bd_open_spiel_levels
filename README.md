# OpenSpiel stones_n_gems Levels
This repo contains levels formatted for the [open_spiel](https://github.com/deepmind/open_spiel) framework `stones_n_gems` game. Included are simple RL levels, and ported levels similar to the ones found in classic games such as Boulder Dash.

## Level Format
The level data is formatted as a comma-separated string. The fist line should contain the number of columns, number of rows, the number of steps before time runs out, and the number of gems required.

The following lines represent the map elements. Each line represents a separate row. For each line, comma-separate each element ID, such that the number of items on each row matches the number of columns specified above. The number of rows should also match.

**Note:** Ensure that there is no trailing new-line at the end of the file.

## Element IDs
The following are the supported elements, along with their IDs. **Note:** Some IDs are not listed, as they are internal elements which represent special elements (falling objects, explosions, etc.)
- Agent -> 0
- Empty -> 1
- Dirt -> 2
- Boulder -> 3
- Diamond -> 5
- Exit Closed -> 7
- Firefly (Up, Left, Down, Right) -> 10, 11, 12, 13
- Butterfly (Up, Left, Down, Right) -> 14, 15, 16, 17
- Brick Wall -> 18
- Steel Wall -> 19
- Magic Wall -> 20
- Blob -> 23
- Closed Red Gate -> 27
- Key Red -> 29
- Closed Blue Gate -> 30
- Key Blue -> 32
- Closed Green Gate -> 33
- Key Green -> 35
- Closed Yellow Gate -> 36
- Key Yellow -> 38
- Nut -> 39
- Bomb -> 41
- Orange (Up, Left, Down, Right) -> 43, 44, 45, 46

## Element Descriptions
A detailed explanation of each element is given below.
- Agent: The agent can move up, down, left, or right. As he moves through dirt, it is removed and left with an empty space. The agent can be killed by falling objects, or enemies such as blobs, fireflies, and butterflies.
- Empty: An empty space, allowing elements to move through.
- Dirt: Prevents objects from falling downwards.
- Boulder: Can fall down, and will explode when impacted on enemies or the agent. Boulders can also roll off rounded objects. Boulders can be pushed horizontally by the agent if there is an empty space on the other side.
- Diamond: Similar to boulders, except the agent gains points when collected. Diamonds need to be collected to complete the level.
- Exit Closed: The end goal for the agent. Must have diamonds collected before it opens.
- Fireflies: Can be oriented up, down, left, or right. Fireflies try to move clockwise. Will explode if a rock falls on it.
- Butterflies: Same as fireflies, but will try to move counter-clockwise. Will turn to diamonds if a rock falls on it
- Oranges: Move either up, left, down, or right. If they hit another object, they randomly start to move in another direction. The agent will die if he runs into a Orange.
- Brick Wall: A rounded wall, which can be consumed if an explosion happens beside.
- Steel Wall: An indestructible wall.
- Magic Wall: Converts diamonds to rocks, and rocks to diamonds if active. Becomes active by dropping a rock through it. Will only remain active for a specified number of steps. There must be room beneath for items to fall through.
- Blob: Will grow into neighbouring cells, if empty or dirt. Blobs have a random chance of growing, as well as the specified direction. If surrounded by elements such as rocks, the blob will turn to diamonds. If blobs grow too large, they will turn to boulders.
- Keys and Gates: Comes in 4 colours; red, blue, green, and yellow. The gates remain closed until the agent collects the corresponding key. Once open, the agent can pass through.
- Nuts: Can fall down like diamonds and boulders. If a boulder falls on it, it will open to reveal a diamond.
- Bombs: Will explode if they fall onto an object, or a rock falls on top of it. The agent can push bombs.
