# Divisible Sum Pairs

Given an array of integers and a positive integer k, determine the number of (i,j) pairs where i < j and ar[i] + ar[j] is divisible by k.

### Example

![image](https://user-images.githubusercontent.com/23621801/184371585-e864bda5-c71e-45fa-8147-2830f0272909.png)


### Function Description

Complete the divisibleSumPairs function in the editor below.

divisibleSumPairs has the following parameter(s):

* int n: the length of array ar 
* int ar[n]: an array of integers
* int k: the integer divisor

### Returns
- int: the number of pairs


### Input Format

The first line contains 2 space-separated integers, n and k.
The second line contains n space-separated integers, each a value of ar[i].

## Constraints

![image](https://user-images.githubusercontent.com/23621801/184373010-a04799fa-6f12-4c80-9581-e4f69bd3a946.png)

### Sample Input

![image](https://user-images.githubusercontent.com/23621801/184373401-ba00f08a-a7bf-4bb3-9b3f-8f23eb5d3df6.png)

### Sample Output

![image](https://user-images.githubusercontent.com/23621801/184373486-cea84b49-dc3b-420c-a379-584f032464b0.png)


### Explanation 


![image](https://user-images.githubusercontent.com/23621801/184374102-1b3c20e4-a1ac-47bc-895f-b2e5618f26eb.png)


```php

<?php

/*
 * Complete the 'divisibleSumPairs' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER n
 *  2. INTEGER k
 *  3. INTEGER_ARRAY ar
 */

function divisibleSumPairs($n, $k, $ar) {
    // Write your code here
    $pairCounter = 0;
    for($i = 0;$i < ($n - 1); $i++){
        for($j = ($i + 1); $j < $n; $j++){
            if((($ar[$i] + $ar[$j]) % $k) === 0){
                $pairCounter++;
            }
        }
    }
    return $pairCounter;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$first_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$n = intval($first_multiple_input[0]);

$k = intval($first_multiple_input[1]);

$ar_temp = rtrim(fgets(STDIN));

$ar = array_map('intval', preg_split('/ /', $ar_temp, -1, PREG_SPLIT_NO_EMPTY));

$result = divisibleSumPairs($n, $k, $ar);

fwrite($fptr, $result . "\n");

fclose($fptr);


```
