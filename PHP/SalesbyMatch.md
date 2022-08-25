# Sales by Match

![image](https://user-images.githubusercontent.com/23621801/186787349-689a1edf-2071-4b1a-9cef-a19eebd0f35c.png)

![image](https://user-images.githubusercontent.com/23621801/186787386-e1742a19-5ece-46bd-a9f4-83dc197e5919.png)

```php

<?php

/*
 * Complete the 'sockMerchant' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER n
 *  2. INTEGER_ARRAY ar
 */

function sockMerchant($n, $ar) {
    // Write your code here
    $aSockets = [];
    foreach($ar as $item){
        if(!isset($aSockets[$item])){
            $aSockets[$item] = 0;
        }
        $aSockets[$item]++;
    }
    $pairCounter = 0;
    foreach($aSockets as $socket){
        $pairCounter += intval($socket/2);
    }
    return $pairCounter;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$n = intval(trim(fgets(STDIN)));

$ar_temp = rtrim(fgets(STDIN));

$ar = array_map('intval', preg_split('/ /', $ar_temp, -1, PREG_SPLIT_NO_EMPTY));

$result = sockMerchant($n, $ar);

fwrite($fptr, $result . "\n");

fclose($fptr);


```
