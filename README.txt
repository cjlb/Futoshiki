/*************************************************/
/*		        Displaying the data			     */
/*************************************************/
The GUI displays the data contained in the Futoshiki Puzzle using images. The project contains a resource file with a series of images that reflect all of the different numbers the tiles need to be able to represent. 
The tiles are displayed in two different variation - editable and non - editable. The editable tiles are white and the non-editable tiles are in a bluey grey colour. The resource file also contains images that reflect
the different constraints present in the grid( row and column, less than and more than). 

The GUI used a gridPane to arrange all of the different elements needed. All of the different elements are arranged on the one central gridPane. In the FutoshikiPuzzle object, three different arrays are used. This means
that the three arrays must be combined into one central gridPane. This is done using modulus calculations to determine where to put what element and what elements need to be left blank. 

If it is determined that the gridPane cell is to display a number cell then the value of the corresponding square is fetched from the Futoshiki object's square array. The getSquare method of the FutoshikiPuzzle is passed
the index of the gridPane but modified to make it reflect the correct position on the square array. The gridPane is twice the size of the square array and is indexed the opposite way to an array (column, row) so the 
getSquare method is passed (jj/2, ii/2). The edit status of the square is then determined as well by using the getEdit method of the FutoshikiSquare. 

A file path is created using the value of the square and it's edit status... e.g if it is editable and has the value of 1 then the filepath would be "./resources/TilePlain-1.png". This image is then fetched and attached
to a button which is inserted into the relevant location on the gridPane. If the tile is not editable then no eventHandler is attached to the button, this means that nothing happens when the user clicks that tile, so the
tile value cannot be changed.

A very similar method is used to display the constraints of the puzzle. If the gridPane index means that a row constraint is needed then the corresponding slot in the rowConstraint array is printed (unless the constraint
array is null in that location) and the string output analysed to determine whether a more than or less than image constraint image is needed. The same process is used for column constraints. The image fetched is 
put into an ImageView and then the imageView is inserted into the gridPane at the correct location. 

This process is repeated whenever a change is made to the values in the grid to ensure the grid reflects the current status of the values contained within the FutoshikiPuzzle squares. This process is contained in the
gridGen method and this is called whenever a change is made to the size or difficulty of the grid or when a large number of square values are set at once (like when the square is restarted). Individual changes are
implented through the changing of the graphics present on the buttons in the gridPane.

/*************************************************/
/*		        Editing the data			     */
/*************************************************/
The user can edit the data present in the squares by clicking the tile (which is a button). Each time an editable tile is clicked the square clicked method is called (through an event handler). This gets the current value
of the square that has been clicked. If the current value is equal to the size of the grid (this means that it is the maximum allowed value) the value is reset to 0. If the value is able to be increased then the value is
incremented by one. Changes to the square value are done using the setSquare method. The filepath reflecting the new value of the square is then calculated and the image on the button changed. The state of the puzzle is
then checked to determine whether the puzzle is now in an illegal state. This is done through the isLegal() method the puzzle. The state output is then updated. 

/*************************************************/
/*		        Additional Features			     */
/*************************************************/
There are a few additonal features present in the game. These are implemented through the row of buttons below the grid. These buttons are: 
New Game
- this allows the user to generate a fresh random grid to play 
Restart
- this restarts the game, putting the grid back into it's original configuration
Hint
- this reveals a square's valid value. It can only be pressed a number of times equivalent to the grid's size. If it is pressed more times than this a dialogue is created informing the user the limit has been reached
Solve
- this fills the grid with a valid solution to the original puzzle presented. 
Finished
- this is a modified version of the core functionality requirement that allows the user to check whether the grid is complete and then ends the game if it is. A dialogue is created allowing a new game to be started or
 the window to be closed.
Quit
- this opens a dialogue where the user can choose to close the window or start a new game
