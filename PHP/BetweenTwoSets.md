# Between Two Sets

There will be two arrays of integers. Determine all integers that satisfy the following two conditions:

1. The elements of the first array are all factors of the integer being considered
2. The integer being considered is a factor of all elements of the second array


These numbers are referred to as being between the two arrays. Determine how many such numbers exist.

![image](https://user-images.githubusercontent.com/23621801/186740949-8666a23f-3e4f-4950-ab97-6581be156f7b.png)

![image](https://user-images.githubusercontent.com/23621801/186740987-37f63785-8e48-4b38-ba77-53a673524e21.png)

## Function Description

Complete the getTotalX function in the editor below. It should return the number of integers that are betwen the sets.

getTotalX has the following parameter(s):

* int a[n]: an array of integers
* int b[m]: an array of integers

### Returns

* int: the number of integers that are between the sets

![image](https://user-images.githubusercontent.com/23621801/186741305-0d97b003-47a5-4456-9cd7-63cc6871e916.png)

![image](https://user-images.githubusercontent.com/23621801/186741327-0baacccf-d8fb-4fe7-8adc-d31bc6125299.png)


Explanation

2 and 4 divide evenly into 4, 8, 12 and 16.
4, 8 and 16 divide evenly into 16, 32, 96.

4, 8 and 16 are the only three numbers for which each element of a is a factor and each is a factor of all elements of b.



```php

<?php

/*
 * Complete the 'getTotalX' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER_ARRAY a
 *  2. INTEGER_ARRAY b
 */

function getTotalX($a, $b) {
    // Write your code here
    $result = 1;
    $aMultiplos = [];
    $sum = 0;
    foreach($a as $key1 => $number1){
        $result = $result * $number1;
        $sum += $number1;
        $flagMultiplo = 1;
        foreach($a as $key2 => $number2){
            if($key1 === $key2){
                continue;
            }
            if(($number1 % $number2)>0){
                $flagMultiplo = 0;
                break;
            }
        }
        if($flagMultiplo){
            $aMultiplos[] = $number1;
        }
    }
    $max  = $result;
    $aMultiplos[] = $result;
    $minB = min($b);
    if(($minB % $max)===0){
        for($i=2;$i<1000;$i++){
            if(($max*$i)>$minB){
                break;
            }
            if(($minB % ($max*$i))===0){
                $aMultiplos[] = ($max*$i);
            }
        }
    }
    if(($minB % $sum) === 0){
        $aMultiplos[] = $sum;
    }
    foreach($aMultiplos as $multiplo){
        if(($minB % $multiplo)===0){
            $aMultiplos[]= $minB;
            break;
        }
    }
    $finalMultiplos = [];
    foreach($aMultiplos as $multiplo){
        $flagMultiplo = 1;
        foreach($b as $item){
            if(($item % $multiplo)>1){
                $flagMultiplo = 0;
                break;
            }
        }
        if($flagMultiplo  && !in_array($multiplo, $finalMultiplos)){
            $finalMultiplos[] = $multiplo;
        }
    }
    return count($finalMultiplos);
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$first_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$n = intval($first_multiple_input[0]);

$m = intval($first_multiple_input[1]);

$arr_temp = rtrim(fgets(STDIN));

$arr = array_map('intval', preg_split('/ /', $arr_temp, -1, PREG_SPLIT_NO_EMPTY));

$brr_temp = rtrim(fgets(STDIN));

$brr = array_map('intval', preg_split('/ /', $brr_temp, -1, PREG_SPLIT_NO_EMPTY));

$total = getTotalX($arr, $brr);

fwrite($fptr, $total . "\n");

fclose($fptr);


```
