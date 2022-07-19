# Staircase 

Staircase detail

This is a staircase of size n = 4 :

![image](https://user-images.githubusercontent.com/23621801/179831863-8e1f1e4a-5c4f-439c-81a4-372a5fbefe17.png)

Its base and height are both equal to . It is drawn using # symbols and spaces. The last line is not preceded by any spaces.

Write a program that prints a staircase of size n.

### Function Description

Complete the staircase function in the editor below.

staircase has the following parameter(s):

* int n: an integer

### Print

Print a staircase as described above.

### Input Format


A single integer, n, denoting the size of the staircase.


### Constraints


0 < n <= 100 


### Output Format

Print a staircase of size  using # symbols and spaces.


Note: The last line must have  spaces in it.



### Sample Input

![image](https://user-images.githubusercontent.com/23621801/179832961-4e5814db-3526-429b-a01c-94a7d02df0c5.png)

### Sample Output

![image](https://user-images.githubusercontent.com/23621801/179833026-bd1e1ca1-5ca6-4b27-a9cd-ba0901e79258.png)


## Explanation

The staircase is right-aligned, composed of # symbols and spaces, and has a height and width of n = 6.


```php

<?php

/*
 * Complete the 'staircase' function below.
 *
 * The function accepts INTEGER n as parameter.
 */

function staircase($n) {
    // Write your code here
    for($i=0;$i<$n;$i++){
        echo str_pad(str_pad('', ($i + 1), "#", STR_PAD_LEFT), $n, ' ', STR_PAD_LEFT)."\n";
    }
}

$n = intval(trim(fgets(STDIN)));

staircase($n);



```
