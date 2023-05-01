Download Link: https://assignmentchef.com/product/solved-blg336e-analysis-of-algorithms-ii-homework-2
<br>
<ul>

 <li>You should write your code in C++ language and use object-oriented approach.</li>

 <li>Write your name and ID on the top of each document that you will upload.</li>

 <li>Compile your code on Linux using g++. You can test your code through ssh.</li>

 <li>Your codes must be compiled with a command like g++ cpp and run with ./a.out test.txt. If you use another instruction please write it in your report.</li>

 <li>You are supposed to prepare a report file where you explain your algorithm and share your test case results in pdf format.</li>

 <li>Use comments to explain your code.</li>

 <li>If you have any questions, please contact me via <u><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="2948425d40181c69405d5c074c4d5c075d5b">[email protected]</a></u></li>

 <li>Submit your homework in a .zip file where it contains all of the necessary .h and .cpp files together with a report in .pdf format.</li>

</ul>




Problem Description

Joseph and Lucy are best friends and they have arranged a travel together two months ago and reserved their flying tickets. However unfortunately, in this two months, they have fought over a small issue and they are not in good terms, so do not want to face each other in any case. Even so, they did not cancel the travel since everything was planned before. They decided to do check-in separately and stay at different hotels during the travel. Also, when going around the city, they do not want to run against each other. That is why we must arrange their routes from their hotels to the their destinations and from destinations to the hotels for one day. The rules are listed below:

<ul>

 <li>The city map is represented as a directed and weighted graph where nodes are places and edges are roads. Edge weights are the lengths of roads.</li>

 <li>Two of the nodes are Joseph’s hotel (JH) and Lucy’s hotel (LH). The other two of the nodes are the destination for Joseph (JD) and destination for Lucy (LD).</li>

 <li>If there is a path from node A to B with length of n, then it takes n minutes to get to B from A. Assume that the speed of the Lucy and Joseph are the same.</li>

 <li>Joseph and Lucy leave their hotels at the same time and they must not be in the same node at the same time.</li>

 <li>They spend 30 minutes at the destination before returning their hotels.</li>

</ul>

You are supposed to find the shortest paths from hotels to destinations and destinations to the hotels that are not intersecting considering the instant locations of Joseph and Lucy.

<h1>PART 1 – Constructing the Graph</h1>

There is an example graph given below where the node 0 is JH, node 5 is JD, node 2 is LH and node 4 is LD. At the right of the graph, the format of the input files is given as the first line gives the number of nodes in the city (N) and the following line contains the hotels and destinations in following order: JH JD LH LD

The lines below gives the edge information as: source node, target node, weight respectively.

You must use the adjacency matrix representation for the graph construction. The txt file for graph input must be given as a command line argument.

<h1>PART 2 – Implementing the algorithm</h1>

You are supposed to implement a shortest path algorithm (i.e. Dijkstra). You need to find 4 shortest paths for each input as:

<ul>

 <li>JH to JD and JD to JH</li>

 <li>LH to LD and LD to LH</li>

</ul>

Remember that edge weights represent how many minutes it takes to get from one node to another and Lucy and Joseph cannot be at the same node at the same time.

So what to do step by step is like this:

<ul>

 <li>Find the shortest paths from hotels to destinations.</li>

 <li>Check if there are any case that Joseph and Lucy are at the same node considering the durations.</li>

 <li>If there is an intersection, find an alternative path which is valid and shortest. You should try to change either Joseph’s or Lucy’s path and choose the better one. If there is no alternative paths for both of them, then print “No solution!” on the screen and terminate the program.</li>

 <li>Then, find the shortest paths from destinations to hotels in the same manner.</li>

</ul>

Note that they have waited at the destination for 30 minutes.

For the example graph given above we can find the shortest paths to destinations as follows:

<table width="206">

 <tbody>

  <tr>

   <td width="55">Node</td>

   <td width="38">0</td>

   <td width="38">1</td>

   <td width="38">4</td>

   <td width="38">5</td>

  </tr>

  <tr>

   <td width="55">Time</td>

   <td width="38">0</td>

   <td width="38">4</td>

   <td width="38">7</td>

   <td width="38">20</td>

  </tr>

  <tr>

   <td width="55"> </td>

   <td width="38"> </td>

   <td width="38"> </td>

   <td width="38"> </td>

   <td width="38"> </td>

  </tr>

  <tr>

   <td width="55">Node</td>

   <td width="38">2</td>

   <td width="38">3</td>

   <td width="38">1</td>

   <td width="38">4</td>

  </tr>

  <tr>

   <td width="55">Time</td>

   <td width="38">0</td>

   <td width="38">10</td>

   <td width="38">15</td>

   <td width="38">18</td>

  </tr>

 </tbody>

</table>

JH (0) to JD (5) :




LH (2) to LD (4):




There is no intersection where Joseph and Lucy are at the same node as you can see in the tables. After waiting for 30 minutes at destinations they go back to the hotels using shortest paths again.

<table width="265">

 <tbody>

  <tr>

   <td width="55">Node</td>

   <td width="35">5</td>

   <td width="35">6</td>

   <td width="35">2</td>

   <td width="35">3</td>

   <td width="35">1</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="55">Time</td>

   <td width="35">50</td>

   <td width="35">56</td>

   <td width="35">58</td>

   <td width="35">68</td>

   <td width="35">73</td>

   <td width="35">79</td>

  </tr>

 </tbody>

</table>

JD (5) to JH (0):




LD (4) to LH (2):

<table width="206">

 <tbody>

  <tr>

   <td width="55">Node</td>

   <td width="38">4</td>

   <td width="38">3</td>

   <td width="38">6</td>

   <td width="38">2</td>

  </tr>

  <tr>

   <td width="55">Time</td>

   <td width="38">48</td>

   <td width="38">49</td>

   <td width="38">56</td>

   <td width="38">58</td>

  </tr>

 </tbody>

</table>




As you can observe in highlighted rows, they met at node 6 at minute 56. So we need to find an alternative second shortest path for Lucy which is 4-3-1-0-2. Because we have no choices for Joseph other than 5-6.

LD (4) to LH (2):

<table width="244">

 <tbody>

  <tr>

   <td width="55">Node</td>

   <td width="38">4</td>

   <td width="38">3</td>

   <td width="38">1</td>

   <td width="38">0</td>

   <td width="38">2</td>

  </tr>

  <tr>

   <td width="55">Time</td>

   <td width="38">48</td>

   <td width="38">49</td>

   <td width="38">54</td>

   <td width="38">60</td>

   <td width="38">68</td>

  </tr>

 </tbody>

</table>

Sample output:

Hint: When comparing the alternative paths for Joseph and

Lucy, please consider

<ul>

 <li>if there is an alternative path</li>

 <li>whether if this new path has any intersections (3) if there are two alternative solutions without intersection, choose the shortest one overall ( J + L ).</li>

</ul>




Note: The test cases will be relatively simple where it is enough to find one alternative path for each person in case of intersection. This will give the result so you do not have to check further. (i.e there will be no cases where there are also intersections for all of the alternative paths, requiring a second iteration for alternative path search.)