<div align="center">
  
  <br/>
 
 
</div>





# Problem Statement
(As per given in E-ROBO contest held by IEEE NIT Patna ,I had participated)


<br/>

-The goal of the task is to use Image Processing and OpenCV techniques to identify shortest route between an origin and a destination as well as detect presence of obstacles if any, on the path supposed to be traversed.
<br/>
-Write a code in python language using openCV techniques to solve the problem.
<br/>
-you are supposed to run and test the code  on sample images provided in the folder “problem_node"
<br/>
-capture screenshots of testing on each test image respectively, and their screenshot should be like this:
<br/>

 <img src="https://github.com/rajutges/SHORTEST-PATH/blob/main/solution_node/Screenshots_solved/path_3.png"/>

-Remember that BLACK BOXES REPRESENT OBSTACLES and they should be avoided while BLUE BOXES REPRESENT THE STARTING AND ENDING Positions.
<br/>

#### What to do?

these thing to be done in the solution folder:

 - code a python code named as "path_code.py"
 - curry and function composition
 - run and test them on sample images provided in the folder “test_images"
 - easier testing and debugging
 - compact and clean code
 - fill all the asked parameters in an excel sheet named “Parameters_Sheet” in the folder named "problem_node"
 - make a folder named "screenshot_solved" which contains the screenshots of tested images as per given in problem statement
 
<br/>

## The command window shall display the following parameters
- Process points: the points which has been processed including obstacle and source and destination.
- Total Number of occupied grids: Number of grids having black or blue 
- Coloured occupied grids: coordinates of blue colored grids
- Total Number of coloured occupied grids: Number of blue colored grids
- Dictionary keys of planned path: source and destination keys
- Coordinates of planned path

<br/>

## Problem_node contains:
- test_images
- parameter_sheet
<br/>
<br/>

## solution_node contains:
- Test_images
- screenshots_solved
- parameter_sheet
- path_code.py code
- different test images

<br/>



## Getting started
-The primary you will need to install python 
- you can use IDE to code such as spyder, jupyter_notebook etc.

<br/>


**Code path_code.py**

**complete code is given in the folder named "solution_node" **

**shortest path**

      #####code are added to get the correcct output as per the task


      import cv2
      import numpy as np
      import time
      import collections  ###used in function
      from skimage.metrics import structural_similarity as ssim

      def shortest_path_algorithm1(grid, start):   
        wall, clear, goal = "#", ".", "B"
        width, height = 10,10
        queue = collections.deque([[start]])
        seen = set([start])
        while queue:
            path = queue.popleft()
            x, y = path[-1]
            if grid[y][x] == goal:
                return path
            for x2, y2 in ((x+1,y), (x-1,y), (x,y+1), (x,y-1)):
                if 0 <= x2 < width and 0 <= y2 < height and grid[y2][x2] != wall and (x2, y2) not in seen:
                    queue.append(path + [(x2, y2)])
                    seen.add((x2, y2))



<br/>




  

<br/>



## Feedback 
Any questions or suggestions?

You are welcome to discuss it on:

[![mail] @ rajutges@gmail.com

<br/>
<br/>


