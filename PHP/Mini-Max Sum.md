# Mini-Max Sum

Given five positive integers, find the minimum and maximum values that can be calculated by summing exactly four of the five integers. 
Then print the respective minimum and maximum values as a single line of two space-separated long integers.

### Example

arr = [1, 3, 5, 7, 9];

The minimum sum is 1 + 3 + 5 + 7 = 16 and the maximum sum is 3 + 5 + 7+ 9 = 24. The function prints

![image](https://user-images.githubusercontent.com/23621801/179842134-ab8cc3d2-2bec-4795-bb03-f9175046e13f.png)

### Function Description

Complete the miniMaxSum function in the editor below.

miniMaxSum has the following parameter(s):

* arr: an array of  integers

### Print


Print two space-separated integers on one line: the minimum sum and the maximum sum of  of  elements.


### Input Format

A single line of five space-separated integers.


### Constraints


1 <= arr[i][j] <= 10^9


### Output Format


Print two space-separated long integers denoting the respective minimum and maximum values that can be calculated by summing exactly four of the five integers. (The output can be greater than a 32 bit integer.)


### Sample Input


![image](https://user-images.githubusercontent.com/23621801/179845168-2b413061-18e9-4880-bf65-1c7c576feba0.png)


### Sample Output

![image](https://user-images.githubusercontent.com/23621801/179845228-6733c1d3-fb4d-4a16-bf24-0cc0e8ef83ef.png)

## Explanation

The numbers are 1, 2, 3, 4 and 5. Calculate the following sums using four of the five integers:

1. Sum everything except 1, the sum is 2 + 3 + 4 + 5.
2. Sum everything except 2, the sum is 1 + 3 + 4 + 5.
3. Sum everything except 3, the sum is 1 + 2 + 4 + 5. 
4. Sum everything except 4, the sum is 1 + 2 + 3 + 5.
5. Sum everything except 5, the sum is 1 + 2 + 3 + 4.


Hints: Beware of integer overflow! Use 64-bit Integer.


```php

<?php

/*
 * Complete the 'miniMaxSum' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function miniMaxSum($arr) {
    // Write your code here
    $arrLength = count($arr);
    $aSums = [];
    for($i=0;$i<$arrLength;$i++){
        $aSums[$i] = 0;
        for($j=0;$j<$arrLength;$j++){
            if($i===$j){
                continue;
            }
            $aSums[$i] += $arr[$j];
        }
    }
    sort($aSums);
    echo $aSums[0]." ".$aSums[($arrLength - 1)];
}

$arr_temp = rtrim(fgets(STDIN));

$arr = array_map('intval', preg_split('/ /', $arr_temp, -1, PREG_SPLIT_NO_EMPTY));

miniMaxSum($arr);


```
