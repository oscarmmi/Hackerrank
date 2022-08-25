# Picking Numbers

Given an array of integers, find the longest subarray where the absolute difference between any two elements is less than or equal to 1.

![image](https://user-images.githubusercontent.com/23621801/186769800-12d31071-685a-45cc-84e8-65b1ba6e387c.png)

## Function Description

Complete the pickingNumbers function in the editor below.

pickingNumbers has the following parameter(s):

* int a[n]: an array of integers

Returns

* int: the length of the longest subarray that meets the criterion

![image](https://user-images.githubusercontent.com/23621801/186770685-fa3bad14-d45a-4d9c-b27c-78d10e9dc197.png)

![image](https://user-images.githubusercontent.com/23621801/186770791-9a6f9d78-e734-4ca0-844e-7b552a6633a7.png)

```php

<?php

/*
 * Complete the 'pickingNumbers' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER_ARRAY a as parameter.
 */

function pickingNumbers($a) {
    // Write your code here
    $arr = [];
    $total = count($a);
    $max = -1;
    foreach($a as $key => $number){
        if(!isset($arr[$key])){
            $arr[$key] = [];
            $arr[$key][] = $number;
        }
        for($i=0;$i<$total;$i++){
            if($key === $i){
                continue;
            }
            if(abs($number-$a[$i])<=1){    
                $flag = 1;  
                foreach($arr[$key] as $item){
                    if(abs($item - $a[$i]) > 1){
                        $flag = 0;  
                        break;
                    }
                }          
                if($flag){
                    $arr[$key][] = $a[$i];    
                }
            }
        }        
        if($max < count($arr[$key])){
            $max = count($arr[$key]);
        }
    }
    return $max;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$n = intval(trim(fgets(STDIN)));

$a_temp = rtrim(fgets(STDIN));

$a = array_map('intval', preg_split('/ /', $a_temp, -1, PREG_SPLIT_NO_EMPTY));

$result = pickingNumbers($a);

fwrite($fptr, $result . "\n");

fclose($fptr);

```
