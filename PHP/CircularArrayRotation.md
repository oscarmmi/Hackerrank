# Circular Array Rotation

John Watson knows of an operation called a right circular rotation on an array of integers. One rotation operation moves the last array element to the first position and shifts all remaining elements right one. To test Sherlock's abilities, Watson provides Sherlock with an array of integers. Sherlock is to perform the rotation operation a number of times then determine the value of the element at a given position.

For each array, perform a number of right circular rotations and return the values of the elements at the given indices.

## Example

![image](https://user-images.githubusercontent.com/23621801/186743054-8b39d6de-a7d8-41d1-a00b-9e89fcddfafc.png)


### Function Description

Complete the circularArrayRotation function in the editor below.

circularArrayRotation has the following parameter(s):

* int a[n]: the array to rotate
* int k: the rotation count
* int queries[1]: the indices to report

## Returns

* int[q]: the values in the rotated a as requested in m

![image](https://user-images.githubusercontent.com/23621801/186743229-88f94000-1185-4286-91de-db61b9c66775.png)

![image](https://user-images.githubusercontent.com/23621801/186743310-596473b2-e7a5-4e19-808b-008bdcfd6422.png)


```php

<?php

/*
 * Complete the 'circularArrayRotation' function below.
 *
 * The function is expected to return an INTEGER_ARRAY.
 * The function accepts following parameters:
 *  1. INTEGER_ARRAY a
 *  2. INTEGER k
 *  3. INTEGER_ARRAY queries
 */

function circularArrayRotation($a, $k, $queries) {
    // Write your code here
    $totalA = count($a);
    $aRotated = [];
    $foundCounter = 0;
    $toBeFound = count($queries);
    foreach($a as $key => $item){
        $futurePos = $key + ($k % $totalA);
        if($futurePos >= $totalA){
            $futurePos -= $totalA;
        }
        if(in_array($futurePos, $queries)){
            $aRotated[$futurePos] = $item;
            $foundCounter++;
        }
        if($foundCounter === $toBeFound){
            break;
        }
    }
    $finalFound = [];
    foreach($queries as $query){
        $finalFound[] = $aRotated[$query];
    }
    return $finalFound;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$first_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$n = intval($first_multiple_input[0]);

$k = intval($first_multiple_input[1]);

$q = intval($first_multiple_input[2]);

$a_temp = rtrim(fgets(STDIN));

$a = array_map('intval', preg_split('/ /', $a_temp, -1, PREG_SPLIT_NO_EMPTY));

$queries = array();

for ($i = 0; $i < $q; $i++) {
    $queries_item = intval(trim(fgets(STDIN)));
    $queries[] = $queries_item;
}

$result = circularArrayRotation($a, $k, $queries);

fwrite($fptr, implode("\n", $result) . "\n");

fclose($fptr);


```
