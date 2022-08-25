# Find Digits

![image](https://user-images.githubusercontent.com/23621801/186750926-60de20c4-fe7d-406f-af3c-ade1ecd89b6b.png)

![image](https://user-images.githubusercontent.com/23621801/186750974-b7fc3902-51d0-427f-bc13-786f72bd13c6.png)

```php

<?php

/*
 * Complete the 'findDigits' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER n as parameter.
 */

function findDigits($n) {
    // Write your code here
    $aN = str_split("$n");
    $counter = 0;
    foreach($aN as $digit){
        $intDigit = intval($digit);
        if(!$intDigit){
            continue;
        }
        if(($n % $intDigit) === 0){
            $counter++;
        }
    }
    return $counter;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$t = intval(trim(fgets(STDIN)));

for ($t_itr = 0; $t_itr < $t; $t_itr++) {
    $n = intval(trim(fgets(STDIN)));

    $result = findDigits($n);

    fwrite($fptr, $result . "\n");
}

fclose($fptr);


```
