# Equalize the Array

![image](https://user-images.githubusercontent.com/23621801/186783829-9fa2b61b-dc54-4c41-9497-dbc2aaad0c79.png)

![image](https://user-images.githubusercontent.com/23621801/186783864-39bb21a4-1b8c-4ecc-aa9a-607a1921406e.png)

```php

<?php

/*
 * Complete the 'equalizeArray' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function equalizeArray($arr) {
    // Write your code here
    $aArr = [];
    $total = count($arr);
    $minDeletes = $total;
    foreach($arr as $key => $number){
        if(!isset($aArr[$key])){
            $aArr[$key] = [];
            $aArr[$key][] = $number;
        }
        foreach($arr as $keyT => $numberT){
            if($key === $keyT){
                continue;
            }
            if($number === $numberT){
                $aArr[$key][] = $numberT;
            }
        }
        $currentTotal = count($aArr[$key]);
        $currentDeletes = $total - $currentTotal;
        if($minDeletes > $currentDeletes){
            $minDeletes = $currentDeletes;
        }
    }
    return $minDeletes;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$n = intval(trim(fgets(STDIN)));

$arr_temp = rtrim(fgets(STDIN));

$arr = array_map('intval', preg_split('/ /', $arr_temp, -1, PREG_SPLIT_NO_EMPTY));

$result = equalizeArray($arr);

fwrite($fptr, $result . "\n");

fclose($fptr);


```
