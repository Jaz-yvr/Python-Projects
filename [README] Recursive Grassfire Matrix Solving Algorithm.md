#**Maze Solver using Grassfire Algorithm**

This Python script implements a maze-solving algorithm using the Grassfire algorithm. Given a matrix representing a maze with obstacles, a start point, and a destination point, the algorithm calculates the shortest path from the start to the destination using a recursive approach.

#__Prerequisites__

Before running the script, ensure you have the following libraries installed:

1. numpy
2. math

Note : You can install these libraries using the following command: pip install numpy

#__Usage__

1. Run the script using a Python interpreter.
2. Follow the prompts to input the required parameters:
    1. Number of rows and columns for the maze (minimum 8).
    2. Percentage of matrix cells that should be obstacles (between 10 and 20).
    3. Column number of the starting block (between 1 and the total number of columns).
    4. Row and column numbers of the destination block (meeting the specified criteria).
3. The script will generate a maze matrix with obstacles and visualize it, then calculate and display the shortest path from the start to the destination.

#__Code Construct__

The script is divided into several parts:
1. Defining Co-ordinate Generator Function: location_generator(row, col) generates random co-ordinates within the given rows and columns.
2. Grassfire Recursive Algorithm: grassfire_recursive(search_map, distance_map, prev_map, x, y, end) implements the core recursive logic of the Grassfire algorithm, updating the distance and previous cell maps.
3. Main Grassfire Algorithm: grassfire(search_map, start, end) initializes distance and previous cell maps, and then uses the recursive function to calculate the shortest path.
4. User Input: The script prompts the user for input values regarding maze dimensions, obstacle percentage, starting point, and destination point.
5. Matrix Initialization: The maze matrix is created with zeros and populated with obstacles.
6. Path Calculation and Visualization: The script calculates the shortest path and visualizes the maze, printing the followed path.

#__Note__

1. The start and destination points are indicated by the value 5 in the matrix.
2. The generated path is printed as a series of co-ordinates and visualized with a 5 in the matrix.

Please ensure to have Python and the required libraries installed before running the script.
