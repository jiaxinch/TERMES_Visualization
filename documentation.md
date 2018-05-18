##### This visualization project is built on *THREE.js*, which included in the directory *js*. *indicator* is the name for the path indicators rendered on the grid, indicating the robot path.

`readBlob()`

`initTrackers()` initializes the tracker vectors. It takes nothing and do not return anything. The `heightTracker[]` is a list of number and keeps track of the current height of the current configuration. The `finalTracker[]` stores the height in each grid for the destination configuration. `cubeTraker[]` will store the instance of the cube object. `cubeFrameTraker[]` will store the frame of each cube, which highlights the sides of the cubes.

`parse()` parses the text input and stores the parse result into different lists. It takes nothing and does not return.

`transLocVec()` transforms the location from text form to a `Vector2`.(the text input location as 1,2 and we need to tranform it to `[1,2]`). The function takes an text string in the format of `x,y` and returns a `Vector2` of `[int, int]`

`init()` is the function that initializes the `scene`
, `camera`, `renderer` .... it takes nothing and does not return. `TrackballControls` is the varaible that controls the 3D movement controlled by the mouse(rotate, tranform and zoom the scene). And this is directly import from the file "*js/TrackballControls*". The speed of rotation, zoom and pan can be controlled by the variables. `grid` in the scene is also initialized.

`initFinalStruc()` calculates the height of cube in each grid according to the instruction we just parsed. The function takes nothing and does not return.

`initInstructions()` traverses all the instructions and `setTimeout` for each instruction. `setTimeout` schedules the functions with different numbers, which indicates the time that the function should be performed. It does not need anything and returns nothing. `framespeed` is a number we set to control the speed of instructions. *The larger the number is, the instructions operates slower.*


`moveFromTo()` takes 