# Beautiful Days at the Movies

![image](https://user-images.githubusercontent.com/23621801/186782327-7b75a02c-888e-47b7-a4c6-e4ea090cd755.png)

![image](https://user-images.githubusercontent.com/23621801/186782408-e544087c-6edf-4d5c-b162-15fda2190c9b.png)

```php

<?php

/*
 * Complete the 'beautifulDays' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER i
 *  2. INTEGER j
 *  3. INTEGER k
 */

function beautifulDays($i, $j, $k) {
    // Write your code here
    $counter = 0;
    for($number=$i;$number<=$j;$number++){
        $aNumber = str_split("$number");
        $sReversedNumber = '';
        foreach($aNumber as $item){
            $sReversedNumber = $item.$sReversedNumber;
        }
        $reversedNumber = intval($sReversedNumber);
        if(!(abs($number -$reversedNumber) % $k)){
            $counter++;
        }
    }
    return $counter;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$first_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$i = intval($first_multiple_input[0]);

$j = intval($first_multiple_input[1]);

$k = intval($first_multiple_input[2]);

$result = beautifulDays($i, $j, $k);

fwrite($fptr, $result . "\n");

fclose($fptr);


```
