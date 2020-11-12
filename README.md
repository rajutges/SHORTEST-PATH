<div align="center">
  
  <br/>
 
 
</div>





# Problem Statement



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

 - code a python code named as "path.py"
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
- path.py code
- different test images

<br/>



## Getting started
-The primary you will need to install python 
- you can use IDE to code such as spyder, jupyter_notebook etc.

<br/>


**Code path.py**

**complete code is given in the folder named "solution_node**

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
**Traversal window**
<br/>
          def traversal_window(image, stepSize, windowSize):
            r =[]
            ###############  slide a window across the image      ############################
            for j in range(0,10):
                for i in range(0,10):
                    r.append((60*i,60*j))
            return r
 ***Check if grids are colored ie not majorly white and termed these grids as full_grids **  *   
           
           for (x, y) in traversal_window(image, stepSize=60, windowSize=(winW, winH)):
                clone = image.copy()
                cv2.rectangle(clone, (x, y), (x + winW, y + winH), (0, 255, 0), 2)
                crop_img = image[y:y + winH,x:x + winW]                 #crop the image
                #list_images[index[0]-1][index[1]-1] = crop_img.copy()
                if (crop_img[30,30,1] < 100):
                    full_grids.append((int(x/60),int(y/60)))
                if (crop_img[30,30,0] == 0):
          #             print("barrier")
                    barrier.append((int(x/60),int(y/60)))
                cv2.imshow("Window", clone)
                cv2.waitKey(1)
                time.sleep(0.0025)
                index[1] = index[1] + 1                            
                if(index[1]>10):
                    index[0] = index[0] + 1
                    index[1] = 1







     




     
<br/>
  ****Compare each image in the list of objects with every other image in the same list****
        x = 0
        source_x = 0
        source_y = 0
        grid = []
        for j in range(0,10):
            s = ""
            for i in range(0,10):
                if image[30 + 60*j,30 + 60*i,2] >230:
                    s = s + "."
                elif image[30 + 60*j,30 + 60*i,2] <30:
                    s = s + "#"
                else:
                    if x==0:
                       sx = i #sourcex
                       sy = j #sourceY
                       s = s + "."
                    else:
                       dx = i
                       dy = j
                       s = s + "B"
                    x = 1
            grid.append(s)




     



     



  

<br/>



## Feedback 
Any questions or suggestions?

You are welcome to discuss it on:

[![mail] @ rajutges@gmail.com

<br/>
<br/>


