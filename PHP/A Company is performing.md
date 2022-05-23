# A company is performing an analysis on the computers at its main office. 


The computers are spaced along a single row. The analysis is performed in the following way: 

1. Choose a contiguous segment of a certain number of computers, starting from the beginning of the row. 
2. Analyze the available hard disk space on each of the computers. 
3. Determine the minimum available disk space within this segment. 

After performing these steps for the first segment, it is then repeated for the next segment, continuing this procedure until the end of the row (for example, 
if the segment size is 4, computers 1 to 4 would be analyzed, then 2 to 5, etc.) Given this analysis procedure, find the maximum available disk space among all 
the minima that are found during the analysis. 


### Example

* n = 3, the number of computers 
* space = [8, 2, 4] 
* x=2, the length of analysis segments 


In this array of computers, the subarrays of size 2 are (8, 2) and [2, 4]. Thus, the initial analysis returns 2 and 2 because those are the minima for the segments. 
Finally, the maximum of these values is 2. Therefore, the answer is 2.

## Function Description

Complete the function *segment* in the editor below.

*segment* has the following parameter(s):

*int x:* the segment length to analyze

*int space[n]:* the available hard disk space on each of the computers


### Returns


*int* the maximum of the minimum values of available hard disk space found while analyzing the computers in segments of numComps

### **Constraints** 

* 1 <= *n* <= 10^6
* 1 <= *x* <= n
* 1<= *space[i]* <= 10^9


## Input Format for Custom Testing

The first line contains an integer, *x*, the segment length for analyzing the row of computers. 
The second line contains an integer, *n*, the size of the array space. Each line of the subsequent lines (where *0 <= i < n*) contains an integer, *space[i]*


## Sample Case 0

### **Sample Input**

![image](https://user-images.githubusercontent.com/23621801/169917439-853f33c2-f2f9-463d-95a4-f0c4873ea839.png)


### **Sample Output**

3


## Explanation

The subarrays of size *x = 1* are [1], [2], [3], [1] and [2]. Because each subarray only contains *1* element, each value is minimal with respect to the subarray it is in. The maximum of these values is *3*. Therefore, the answer is *3*.



