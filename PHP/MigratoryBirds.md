# Migratory Birds

Given an array of bird sightings where every element represents a bird type id, determine the id of the most frequently sighted type. If more than 1 type has been spotted that maximum amount, return the smallest of their ids.

### Example

![image](https://user-images.githubusercontent.com/23621801/184927666-e9c86021-1d39-447d-b11a-1c59cd815f88.png)

### Function Description

Complete the migratoryBirds function in the editor below.

migratoryBirds has the following parameter(s):

* int arr[n]: the types of birds sighted

### Returns

* int: the lowest type id of the most frequently sighted birds


### Input Format

The first line contains an integer,n , the size of arr.
The second line describes arr as n space-separated integers, each a type number of the bird sighted.

### Constraints

![image](https://user-images.githubusercontent.com/23621801/184927960-0d4fdedf-763f-4ea9-8b0c-7dc4d0398b30.png)

### Sample Input 0

![image](https://user-images.githubusercontent.com/23621801/184928022-4cb77b47-f0f5-41fe-aeb4-fee2d21b253f.png)


### Sample Output 0


![image](https://user-images.githubusercontent.com/23621801/184928068-45b3dd84-23ab-41f6-b620-e6dcf75b4f9e.png)


### Explanation 0

![image](https://user-images.githubusercontent.com/23621801/184928142-5b18fad2-c11b-4378-81e9-c3e032763866.png)





```php

<?php

/*
 * Complete the 'migratoryBirds' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function migratoryBirds($arr) {
    // Write your code here
    $aIds = [];
    $currentValue = 0;
    $max = -1;
    foreach($arr as $item){
        if(!isset($aIds[$item])){
            $aIds[$item] = 0;
        }
        $aIds[$item]++;
        $currentValue = $aIds[$item];
        if($currentValue > $max){
            $max = $currentValue;
        }
    }
    $aMax = [];
    foreach($aIds as $key => $item){
        if($item == $max){
            $aMax[] = $key;
        }
    }
    sort($aMax);
    return $aMax[0];
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$arr_count = intval(trim(fgets(STDIN)));

$arr_temp = rtrim(fgets(STDIN));

$arr = array_map('intval', preg_split('/ /', $arr_temp, -1, PREG_SPLIT_NO_EMPTY));

$result = migratoryBirds($arr);

fwrite($fptr, $result . "\n");

fclose($fptr);


```
