# Library Fine

![image](https://user-images.githubusercontent.com/23621801/186750057-e358be24-9368-4087-9bef-9334d69fd97e.png)

![image](https://user-images.githubusercontent.com/23621801/186750090-98477a90-66b4-4925-9c66-b0c6b6a92b71.png)

```php

<?php

/*
 * Complete the 'libraryFine' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER d1
 *  2. INTEGER m1
 *  3. INTEGER y1
 *  4. INTEGER d2
 *  5. INTEGER m2
 *  6. INTEGER y2
 */

function libraryFine($d1, $m1, $y1, $d2, $m2, $y2) {
    // Write your code here
    if($y1 > $y2){
        return 10000;
    }
    if($m1 > $m2 && ($y1 === $y2)){
        return 500 * ($m1 - $m2);
    }
    if($d1 > $d2 && ($m1 === $m2) && ($y1 === $y2)){
        return 15 * ($d1 - $d2);
    }
    return 0;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$first_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$d1 = intval($first_multiple_input[0]);

$m1 = intval($first_multiple_input[1]);

$y1 = intval($first_multiple_input[2]);

$second_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$d2 = intval($second_multiple_input[0]);

$m2 = intval($second_multiple_input[1]);

$y2 = intval($second_multiple_input[2]);

$result = libraryFine($d1, $m1, $y1, $d2, $m2, $y2);

fwrite($fptr, $result . "\n");

fclose($fptr);

```
