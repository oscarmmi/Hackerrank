# Counting Valleys

![image](https://user-images.githubusercontent.com/23621801/185029564-ae5a8c5d-0a96-41e3-bfc8-c21856d8b34d.png)


![image](https://user-images.githubusercontent.com/23621801/185029614-d6e32568-0fa6-49ec-81e3-1e9dd9b8f60e.png)

![image](https://user-images.githubusercontent.com/23621801/185029654-d4baa49a-6794-42e1-b783-41e6d63c0ec2.png)


```php

<?php

/*
 * Complete the 'countingValleys' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER steps
 *  2. STRING path
 */

function countingValleys($steps, $path) {
    // Write your code here
    $aSteps = str_split($path, 1);
    $counter = 0;
    $valleyCounter = 0;
    $flagValley = 0;
    foreach($aSteps as $step){
        if(strtoupper($step) == 'D'){
            $counter--;
        }else if(strtoupper($step) == 'U'){
            $counter++;
        }
        if(!$flagValley && $counter<0){
            $valleyCounter++;
            $flagValley = 1;
        }
        if($flagValley && $counter>=0){
            $flagValley = 0;
        }
    }
    return $valleyCounter;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$steps = intval(trim(fgets(STDIN)));

$path = rtrim(fgets(STDIN), "\r\n");

$result = countingValleys($steps, $path);

fwrite($fptr, $result . "\n");

fclose($fptr);


```
