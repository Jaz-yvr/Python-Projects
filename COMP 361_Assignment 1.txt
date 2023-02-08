

import numpy as np
import math

#defining a function to generate co-ordinates

def location_generator(row, col):
    row = np.random.randint(0,row)
    col = np.random.randint(0,col)
    location = [row,col]
    return (location)

# grassfire using recursion    

def grassfire_recursive(search_map, distance_map, prev_map, x, y, end):
    m, n = len(search_map), len(search_map[0])
    if x < 0 or x >= m or y < 0 or y >= n or search_map[x][y] == 1:
        return
    distance = distance_map[x][y] + 1
    if (x > 0 and distance_map[x-1][y] > distance):
        distance_map[x-1][y] = distance
        prev_map[x-1][y] = (x, y)
        grassfire_recursive(search_map, distance_map, prev_map, x-1, y, end)
    if (x < m-1 and distance_map[x+1][y] > distance):
        distance_map[x+1][y] = distance
        prev_map[x+1][y] = (x, y)
        grassfire_recursive(search_map, distance_map, prev_map, x+1, y, end)
    if (y > 0 and distance_map[x][y-1] > distance):
        distance_map[x][y-1] = distance
        prev_map[x][y-1] = (x, y)
        grassfire_recursive(search_map, distance_map, prev_map, x, y-1, end)
    if (y < n-1 and distance_map[x][y+1] > distance):
        distance_map[x][y+1] = distance
        prev_map[x][y+1] = (x, y)
        grassfire_recursive(search_map, distance_map, prev_map, x, y+1, end)

def grassfire(search_map, start, end):
    m, n = len(search_map), len(search_map[0])
    distance_map = [[float('inf') for _ in range(n)] for _ in range(m)]
    prev_map = [[None for _ in range(n)] for _ in range(m)]
    distance_map[start[0]][start[1]] = 0
    grassfire_recursive(search_map, distance_map, prev_map, start[0], start[1], end)

    path = []
    curr_pos = end
    while prev_map[curr_pos[0]][curr_pos[1]] is not None:
        path.append(curr_pos)
        curr_pos = prev_map[curr_pos[0]][curr_pos[1]]
    path.append(start)
    print(str(len(path)-1) + " steps needed to reach destination")
    return list(reversed(path))



#setting up row and column values higher than 8

row = input ("Please enter the number of rows :") 
row = int(row)
while row < 8 :
    print ("Enter value higher than 8")
    row = input ("Please enter the number of rows :") 
    row = int(row)

col = input ("Please enter the number of columns :") 
col= int(col)
while col < 8 :
    print ("Enter value higher than 8")
    col = input ("Please enter the number of rows :") 
    col = int(col)


## setting the bounds for obstacle cells

percentage = input ("What percent of the matrix do you wish to be an obstacle ?")
percentage = float(percentage)
while percentage  :  
    if percentage < 10:
        print("needs value higher than 10")
        percentage = input ("What percent of the matrix do you wish to be an obstacle ?")
        percentage = float(percentage)
    elif percentage > 20:
        print("needs value less than 20")
        percentage = input ("What percent of the matrix do you wish to be an obstacle ?")
        percentage = float(percentage)
    else :
        break
obstacle_Blocks = row * col * percentage/float(100)
obstacle_Blocks = math.ceil(obstacle_Blocks)
print  ("There will be " + str(obstacle_Blocks) +" obstacle blocks")

##initializing the starting block, Note: count starts from 1 and not 0, not in index format

start_col = input ("Enter the column number of the starting block :")
start_col = int(start_col)
while (start_col) > col or (start_col) < 1 :
    print ("enter a valid number above 1 and below "+ str(col) )
    start_col = input ("Enter the column number of the starting block :")
    start_col = int(start_col)


##Destination Block, Note: assuming counting is going 1 to row, not in index format.

dest_row = input ("Please enter the destination block row number :") 
dest_row = int(dest_row)
row_ceil = math.ceil(row/float(2))
while (dest_row) < row_ceil or (dest_row) > row :
    print ("Enter a value higher than " + str(row_ceil) + " and less than "+ str(row)) 
    dest_row = input ("Please enter the destination block row number :") 
    dest_row = int(dest_row)
    
dest_col = input ("Please enter the destination block column number :")
dest_col = int(dest_col)
col_ceil = math.ceil((2*col)/float(3))
while dest_col > col or dest_col < col_ceil :
    print ("Enter a value higher than " + str(col_ceil) + " and less than " +str(col)) 
    dest_col = input ("Please enter the destination block column number :")
    dest_col = int(dest_col) 

dest_row = math.ceil(dest_row)
dest_col = math.ceil(dest_col)

#generating the matrix wit 0's  

matrix = [] 
for i in range(row):
    # Create a new row as a list
    rows = []
    for j in range(col):
        # Append the elements to the row
        rows.append(0)
    # Append the row to the matrix
    matrix.append(rows)


#filling the matrix with obstacles
for a in range (obstacle_Blocks) :
    temp_block = location_generator(row,col)
    matrix[temp_block[0]][temp_block[1]] = 1
    
#overriding the start and the destination spots; starts from 1
matrix[dest_row-1][dest_col-1] = 5
matrix[0][start_col-1] = 5

# Print the 2D structure with the obstacles
for rows in matrix:
    print(rows)
print (" ")
#solving the maze and storing the list and printing it

start = [0, start_col-1 ]
end = [dest_row-1 , dest_col-1 ]
distance = grassfire(matrix, start, end)
print(" ")
print ("The path followed was" + str(distance))

#tracing the followed path

for a2 in range(len(distance)) :
    tracker = distance[a2]
    matrix[tracker[0]][tracker[1]] = 5

#new matrix with the path    
print(" ")
for rows in matrix:
    print(rows)
