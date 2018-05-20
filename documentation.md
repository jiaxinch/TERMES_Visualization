## this documentation is for the visualization of TERMES project. This is a *single agent* robot construction project.
##### Glossary and other
1. This visualization project is built on *THREE.js*, which included in the directory *js*.
2. the robot has a front face, which is painted blue in this version. The robot can only moves in the direction of its face and can only pick a block that is in front of its face. Rotation is implemented in the move function.
3. **up** and **down**, **left** and **right** is created base on the default grid position. And we assign numbers to all the directions: up is 0, right is 1, down 2, left 3
3. **indicator** is the name for the path indicators rendered on the grid, indicating the robot path.
4. **main grid** refers to the grid where the building animation takes place.
5. **small grid** and **preview grid** refers to the grid that places on the bottom of the page and shows a preview of the result construction.
6. **grid position** and **grid location** refers to the coordinate on the grid. It is a 2-tuple of `int`. **worldPosition** refers to the position in the rendering world, which is a 3-tuple of `double`.

`readBlob()`

`initTrackers()` initializes the tracker vectors. It takes nothing and do not return anything. The `heightTracker[]` is a list of number and keeps track of the current height of the current configuration. The `finalTracker[]` stores the height in each grid for the destination configuration. `cubeTraker[]` will store the instance of the cube object. `cubeFrameTraker[]` will store the frame of each cube, which highlights the sides of the cubes.

`parse()` parses the text input and stores the parse result into different lists. It takes nothing and does not return.

`transLocVec()` transforms the location from text form to a `Vector2`.(the text input location as 1,2 and we need to tranform it to `[1,2]`). The function takes an text string in the format of `x,y` and returns a `Vector2` of `[int, int]`

`init()` is the function that initializes the `scene`, `camera`, `renderer` .... it takes nothing and does not return. `TrackballControls` is the varaible that controls the 3D movement controlled by the mouse(rotate, tranform and zoom the scene). And this is directly import from the file "*js/TrackballControls*". The speed of rotation, zoom and pan can be controlled by the variables. `grid` in the scene is also initialized.

`initFinalStruc()` calculates the height of cube in each grid according to the instruction we just parsed. The function takes nothing and does not return.

`initInstructions()` traverses all the instructions and `setTimeout` for each instruction. `setTimeout` schedules the functions with different numbers, which indicates the time that the function should be performed. It does not need anything and returns nothing. `framespeed` is a number we set to control the speed of instructions. *The larger the number is, the instructions operates slower.*

`renderSmallCubes()` is the function that render cubes in the smaller preview window. It renders the final structure according to the `finalTracker[][]`. it takes nothing and does not return.

`moveFromTo()` takes two `Vector3`, one is the *from* location and the other is the *other* location. The function moves the robot from the *from* location to the *to* location. And the function return nothing.

`moveRight()`, `moveLeft()`,`moveUp()`, `moveDown()`calls `moveOneGridUp` and `moveOneGridRight` to move the grid.

`calculateSmallPosition()` is the function that takes in the location on the grid and calculate the corresponding world position on the *small grid*. Similar to `calculateWorldPosition()`, this function calculates position on the *preview grid* instead of the *main grid*.

`calculateWorldPosition()` takes a *gridPosition* and transforms it into a worldPosition and returns a `Vector3` of the world position.

`renderACube()` takes three world position numbers and render a cube in the corresponding position on the *main grid*. And then return a `Vector2` with first element contains the cube instance and the second element wireframe instance.

`renderASmallCube()` is similar to `renderACube()`, takes three world position numbers and render a cube in the corresponding position on the *preview grid*. And then return a `Vector2` same to the `renderACube()`.

`renderIndicators()` renders path indicators in the array according to the type of the indicators. There are two types *a* and *r*. It takes an array of positions and type of indicators and returns nothing

`renderAIndicator()` renders a path indicators according to the type of the indicators. It takes position of X and y and type, and returns nothing.

`renderAIndicatorHelper()` takes x, y and z position and type of indicators. This function helps render the path indicators. The function returns the indicator so that we can delete the path indicator later.

`removeIndicators()` is the function that removes all the indicators from the scene and delete all the indicators after robot reach the sides of the grid. It does not need anything and return nothing.

`removeLastIndicator()` is the function removes the last indicator on the path. It is used when the robot remove a block which has a indicator on its head. When the robot removes the block, the indicator there should also be removed. it takes nothing and returns nothing.

`renderRobot()` is the function that renders the robot according to the variable `robotLocation`, which is a **grid position**. This function takes in the **grid position** and render the robot and its wireframe at that position.

`removeRobot()` is the function that removes both robot and its wireframe.

`pickACube()` is the function that renders a cube on the head of the robot. It is called when the robot reach the sides of the grid.

`render()` is the function that renders the scene. Whenever there are changes to the scene, `render()` is called to show the changes on the screen.

`smallWindowRender()` is the function that renders the small window.

`animate()` is the function that applys the *pan* *zoom* action to the screen.

`moveOneGridRight()` takes a number, 1 or -1. if 1, moves right else move left. if the robot is moving a cube, the cube will move with the robot. if the robot face left, when `moveOneGridRight(1)`, it will face right and then move one grid right.
`moveOneGridUp()` is basically the same thing as `moveOneGridRight`. if takes 1, move up, else move down.


`rotate()` is the function that rotates the **robot**. it takes two `int` number. once called, the robot will rotate from *from* direction to *to* direction.

`removePickedBlock()` removes the block on the robots' head.

`putBlockDown()` takes a **grid position** that the block should be placed. it first check whether the parameter position is distance 1 away and rotates the robot to the direction so it can put the block down. Then render the block at the desired location and remove the block on robots head.

`putBlockUp()` is the function that enable the robot remove a block from the building and put the block on its head. It is basically the same thing as the `putBlockDown()`. 
