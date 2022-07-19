# Diagonal Difference 

Given a square matrix, calculate the absolute difference between the sums of its diagonals.

For example, the square matrix  is shown below:

![image](https://user-images.githubusercontent.com/23621801/179769219-eb50c61f-d558-491b-ae41-7c4485267bd2.png)

The left-to-right diagonal = 1 + 5 + 9 = 15 . The right to left diagonal = 3 + 5 + 9 = 17. Their absolute difference is | 15 - 17 | = 2.

## Function description

Complete the diagonalDifference function in the editor below.

diagonalDifference takes the following parameter:

* int arr[n][m]: an array of integers

### Return

* int: the absolute diagonal difference

### Input Format

The first line contains a single integer, n , the number of rows and columns in the square matrix arr.
Each of the next n  lines describes a row, arr[i] , and consists of n space-separated integers arr[i][j].

### Constraints

* -100 <= arr[i][j] <= 100

### Output Format

Return the absolute difference between the sums of the matrix's two diagonals as a single integer.


## Sample Input

![image](https://user-images.githubusercontent.com/23621801/179775145-b4bb70e6-ee89-4018-bad4-7513e5d0617c.png)

### Sample Output

![image](https://user-images.githubusercontent.com/23621801/179775355-24611e84-345a-4e56-bc22-93972da56094.png)


### Explanation

The primary diagonal is:

![image](https://user-images.githubusercontent.com/23621801/179775783-186da658-fa9e-4a43-9659-7b4692f781ba.png)


Sum across the primary diagonal: 11 + 5 - 12 = 4


The secondary diagonal is:


![image](https://user-images.githubusercontent.com/23621801/179778930-42fe59f2-568e-4396-925a-69178141fd3b.png)


Sum across the secondary diagonal: 4 + 5 + 10 = 19


Difference: |4 - 19| = 15

Note: |x| is the absolute value of x



```php

<?php

/*
 * Complete the 'diagonalDifference' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts 2D_INTEGER_ARRAY arr as parameter.
 */

function diagonalDifference($arr) {
    // Write your code here
    $number = count($arr);
    $diagonal1 = 0;
    for($i=0; $i < $number; $i++){
        $diagonal1 += $arr[$i][$i];
    }
    $diagonal2 = 0;
    $counter = 0;
    for($i = ($number - 1); $i >= 0; $i = ($i - 1)){
        $diagonal2 += $arr[$counter][$i];
        $counter++;
    }
    return abs($diagonal1 - $diagonal2);
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$n = intval(trim(fgets(STDIN)));

$arr = array();

for ($i = 0; $i < $n; $i++) {
    $arr_temp = rtrim(fgets(STDIN));

    $arr[] = array_map('intval', preg_split('/ /', $arr_temp, -1, PREG_SPLIT_NO_EMPTY));
}

$result = diagonalDifference($arr);

fwrite($fptr, $result . "\n");

fclose($fptr);



```
