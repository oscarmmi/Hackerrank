# Number Line Jumps

You are choreographing a circus show with various animals. For one act, you are given two kangaroos on a number line ready to jump in the positive direction (i.e, toward positive infinity).


* The first kangaroo starts at location x1 and moves at a rate of v1 meters per jump.
* The second kangaroo starts at location x2 and moves at a rate of v2 meters per jump.

You have to figure out a way to get both kangaroos at the same location at the same time as part of the show. If it is possible, return YES, otherwise return NO.

![image](https://user-images.githubusercontent.com/23621801/183940088-334c0f7a-6670-4c96-97b5-805a16d13188.png)


After one jump, they are both at x = 3, ( x1 + v1 = 2 + 1, x2 + v2 = 1 + 2), so the answer is YES.

### Function Description

Complete the function kangaroo in the editor below.

kangaroo has the following parameter(s):

* int x1, int v1: starting position and jump distance for kangaroo 1
* int x2, int v2: starting position and jump distance for kangaroo 2


### Returns

* string: either YES or NO


### Input Format

A single line of four space-separated integers denoting the respective values of x1, v1, x2, and v2.


![image](https://user-images.githubusercontent.com/23621801/183942578-670c4e8c-f0a0-4715-b6d7-22bba1be912f.png)

From the image, it is clear that the kangaroos meet at the same location (number 12  on the number line) after same number of jumps ( jumps), and we print YES.

![image](https://user-images.githubusercontent.com/23621801/183942739-c75f677b-3513-4206-9a82-08fc3dc1f9e4.png)


### Explanation 1


The second kangaroo has a starting location that is ahead (further to the right) of the first kangaroo's starting location (i.e., x2 > x1). 
Because the second kangaroo moves at a faster rate (meaning v2 > v1) and is already ahead of the first kangaroo, the first kangaroo will never be able to catch up. 
Thus, we print NO.


