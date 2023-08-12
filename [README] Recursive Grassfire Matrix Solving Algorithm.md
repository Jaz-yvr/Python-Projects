# Recursive Grassfire Matrix Solving Algorithm
This Python script implements a maze-solving algorithm using the Grassfire algorithm. Given a matrix representing a maze with obstacles, a start point, and a destination point, the algorithm calculates the shortest path from the start to the destination using a recursive approach.

Prerequisites
Before running the script, ensure you have the following libraries installed:

numpy
math
You can install these libraries using the following command:

bash
Copy code
pip install numpy
Usage
Run the script using a Python interpreter.
Follow the prompts to input the required parameters:
Number of rows and columns for the maze (minimum 8).
Percentage of matrix cells that should be obstacles (between 10 and 20).
Column number of the starting block (between 1 and the total number of columns).
Row and column numbers of the destination block (meeting the specified criteria).
The script will generate a maze matrix with obstacles and visualize it, then calculate and display the shortest path from the start to the destination.
Code Structure
The script is divided into several parts:

Defining Co-ordinate Generator Function: location_generator(row, col) generates random co-ordinates within the given rows and columns.

Grassfire Recursive Algorithm: grassfire_recursive(search_map, distance_map, prev_map, x, y, end) implements the core recursive logic of the Grassfire algorithm, updating the distance and previous cell maps.

Main Grassfire Algorithm: grassfire(search_map, start, end) initializes distance and previous cell maps, and then uses the recursive function to calculate the shortest path.

User Input: The script prompts the user for input values regarding maze dimensions, obstacle percentage, starting point, and destination point.

Matrix Initialization: The maze matrix is created with zeros and populated with obstacles.

Path Calculation and Visualization: The script calculates the shortest path and visualizes the maze, printing the followed path.

Note
The start and destination points are indicated by the value 5 in the matrix.
The generated path is printed as a series of co-ordinates and visualized with a 5 in the matrix.
Please ensure to have Python and the required libraries installed before running the script.
