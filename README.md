Download Link: https://assignmentchef.com/product/solved-comp472-artificial-intelligence-assignment-1
<br>
<h1>1.     Montreal Crime Analytics</h1>

<strong> </strong>

In this project, we locate four coordinates ([longitude, latitude]) (-73.59, 45.49), (-73.55, 45.49), (-73.55, 45.53), (-73.59, 45.53) in the center of Montreal downtown area. The blue square in the screenshot (see Figure 1.1) shows the located area. All the crime data in this area are saved in the file “<em>crime_dt.shp</em>”, which includes all the crime data considered at different points. The dataset is fetched and modified from the City of Montreal’s open data portal.










<em>Figure 1.1 Located area in the center of Montreal map </em>

<strong> </strong>

Using this located area, you need to generate grids in this area to compute the crime rate statistics in each grid. The size of each grid could be changed due to the distribution of crime; however, your program should be flexible to change the size of each grid when it is required.




For example, in Figure 1.2 each grid has the size of 0.003 * 0.003 in (a) and 0.002*0.002 in (b). As the size of grids grows, the results of distribution may be focused on each grid evenly. Therefore, to ensure and display the accuracy of the data, smaller size less or equal to 0.002* 0.002 of each grid is recommended.







(a) size of each grid 0.003*0.003                                   (b)  size of each grid 0.002*0.002




<em>Figure 1.2 distribution of grids with different sizes </em>




Crime rates are considered as the number of points in each block defined by the grid. The crime rates need to be calculated using statistics such as total count, mean, standard deviation in your results. A threshold of crime rate is introduced to define the high crime rate blocks and low crime rate blocks in the area selected. The threshold would be arbitrarily chosen. For example, if you choose the threshold using the median (the crime rate of a block higher than 50% of the crime rates of total blocks), blocks with the crime rate higher than median are labelled in yellow (highly risky blocks), and blocks with the crime rate lower than median are labelled in purple (less risky blocks). According to different thresholds, the crime rates in the located area will be presented as the following graphs.







(a)  threshold 1                                   (b)  threshold 2                               (c)  threshold 3

<em>Figure 1.3 Using different thresholds to present the crime rates on the map </em>

<strong> </strong>

<strong><u>Definition of Threshold</u> </strong>

Assuming all the grids in your program have different number of crime rates, all the numbers are in an descending order. Therefore, if the threshold = 50%, we take the numbers that are greater or equal to median number marked as block area; if the threshold = 75%, we take the numbers that have index (=1, 2…) less or equal to total number of grids*(1-75%) marked as block area; if the threshold = 90%, we take the numbers have index less or equal to total number of grids*(1-90%) marked as block area.




For example, we have the sequence {10, 9, 8, 7, 6, 5, 4, 3, 2, 1}

If the threshold = 50%, the numbers {10, 9, 8, 7, 6} are considered as blocks; If the threshold = 75%, the numbers {10, 9} are considered as blocks; If the threshold = 90%, the numbers {10} are considered as blocks.

<strong> </strong>

<h1>2.   Your Task</h1>

In this assignment, you will generate the crime risk map based on the crime rates and implement an A* heuristic search algorithm to find an optimal path between two coordinates on the map.




<h2>2.1  Display Results</h2>

<ol>

 <li>Your program should be able to read the map area located in the area of four coordinates ([longitude, latitude]) (-73.59, 45.49), (-73.55, 45.49), (-73.55, 45.53), (-73.59, 45.53) in the center of Montreal downtown area.</li>

 <li>Your program can draw the grids and generates graph indicating the crime rates in each grid using the “<em>shp</em>” file.</li>

</ol>

(<strong>Please note:</strong> to load and read the “<em>crime_dt.shp</em>” file, the other four files “<em>crime_dt.cpg”, “crime_dt.dbf”, “crime_dt.prj”, and “crime_dt.shx”</em> in the same folder named “Shape” attached should be put in the same local path.)

<ol start="3">

 <li>Compute the number of total crimes in each grid, average and standard deviation of all grids and generate graphs displaying the crime rates using different colors based on the local area.</li>

 <li>Using the graph, which includes yellow blocks considers as obstacles, in the example above illustrates the high crime rate areas (see Figure 1.3), your program should implement an A* heuristic algorithm to find an optimal path from any two coordinates that the user prompt within the map.</li>

</ol>

Please note your path should avoid all the high-risk areas in your map and the path could be changed according to the different chosen thresholds. Your program cannot call any existing searching functions to find the optimal path. You have to implemented your original heuristic algorithm.

<ol start="5">

 <li>When you design the A* heuristic method and draw the optimal path on the map, here are some rules that should be followed:

  <ol>

   <li>Try to avoid the block areas.</li>

   <li>All the edges between two block areas and its diagonal are forbidden (see Fig(1) below).</li>

   <li>All the edges between one block (yellow) and one low crime rate area (blue) are accessible and the cost of this edge is 1.3 (see Fig(2) below).</li>

   <li>All the edges between two low crime rate areas and diagonal are accessible. The cost of this edge = 1 and diagonal cost = 1.5 (see Fig(3) below).</li>

  </ol></li>

</ol>

<sub>                        </sub>

<ol>

 <li>All the boundary edges of the map are considered as inaccessible.</li>

 <li>If the point P is located inside one grid, use the lowest coordinates in this grid as the location. This coordinate is the left bottom coordinates of this grid.</li>

</ol>




<h2>2.2  Programming Details</h2>

<ol>

 <li>To implement this project, you must use Python.</li>

</ol>

Please note the libraries can be used but not limited to Numpy, Pandas, Pyshp, ScikitLearn. Please list all the required libraries of your program in README.txt.

<ol start="2">

 <li>Your program must be able to find the optimal path at most 10 seconds.</li>

</ol>

If there is no path will be found from the current map, e.g. the destination are surrounded by blocks, your program should output the message <em>“Due to blocks, no path is found. Please change the map and try again”</em>; Otherwise, if the path exists, your program should measure the time when starting to find the optimal path. If it takes more than 10 seconds, your program should output the message <em>“Time is up. The optimal path is not found.”</em>

<ol start="3">

 <li>It is not necessary to have a fancy user-interface. A simple command-line interface with a direct output is sufficient.</li>

 <li>All the results listed in Section <em>1 Display Details </em>should be presented in GUI and it should be easy to change the input grid size and the chosen threshold using the command-line interface when it is required.</li>

</ol>




<h1>3.   Deliverables</h1>

<h2>3.1  Demos</h2>

Assignment 1 will be demonstrated using Zoom. You will demo the program that was uploaded as the official submission on or before the due date. The schedule of the demos will be posted on Moodle. No special preparation is necessary for the demo (no slides or presentation needed). Your TA will ask you questions about your code, and you will have to answer all the questions. Your code will be checked for similarity.

<strong> </strong>

<h2>3.2  Grading Scheme</h2>

<strong> </strong>

<table width="575">

 <tbody>

  <tr>

   <td width="169"><strong>Grading Criteria </strong></td>

   <td width="349"><strong>Description </strong></td>

   <td width="57"><strong>Points </strong></td>

  </tr>

  <tr>

   <td rowspan="4" width="169"><strong>Map </strong><strong>(5 pts) </strong></td>

   <td width="349">Draw the grids</td>

   <td width="57">1 pt</td>

  </tr>

  <tr>

   <td width="349">Generate the map by crime rates</td>

   <td width="57">2 pts</td>

  </tr>

  <tr>

   <td width="349">Apply different threshold by prompting user for inputs</td>

   <td width="57">1 pt</td>

  </tr>

  <tr>

   <td width="349">Display the number of total crimes in each grid, average and standard deviation of all grids</td>

   <td width="57">1 pt</td>

  </tr>

  <tr>

   <td rowspan="2" width="169"><strong>A* Heuristic Method (10 pts) </strong></td>

   <td width="349">Heuristic function, total cost, admissibility</td>

   <td width="57">4 pts</td>

  </tr>

  <tr>

   <td width="349">Follow the rules in 2.1.5 to design heuristic method</td>

   <td width="57">6 pts</td>

  </tr>

  <tr>

   <td rowspan="2" width="169"><strong>Optimal Path (3 pts) </strong></td>

   <td width="349">Find the path from any 2 points by prompting user for inputs</td>

   <td width="57">2 pts</td>

  </tr>

  <tr>

   <td width="349">Execution time and instant outputs</td>

   <td width="57">1 pt</td>

  </tr>

  <tr>

   <td width="169"><strong>Code Quality </strong></td>

   <td width="349">Necessary comments, readability and clarity</td>

   <td width="57">1 pt</td>

  </tr>

  <tr>

   <td width="169"><strong>README.txt </strong></td>

   <td width="349">Instructions on how to run your program and list of libraries</td>

   <td width="57">1 pt</td>

  </tr>

  <tr>

   <td width="169"><strong>Total </strong></td>

   <td width="349"> </td>

   <td width="57">20 pts</td>

  </tr>

 </tbody>

</table>


