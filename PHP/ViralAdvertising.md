# Viral Advertising

![image](https://user-images.githubusercontent.com/23621801/186781727-f8950ddf-f6df-407f-b7fe-581b65245f37.png)

![image](https://user-images.githubusercontent.com/23621801/186781768-5b279299-a4d1-437c-a602-b1e95820e7ef.png)

```php

<?php

/*
 * Complete the 'viralAdvertising' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER n as parameter.
 */

function viralAdvertising($n) {
    // Write your code here
    $seed = 5;
    $liked = 0;
    for($i=1;$i<=$n;$i++){
        $likedByDay = floor($seed / 2);
        $liked += $likedByDay;
        $seed = $likedByDay * 3;
    }
    return $liked;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$n = intval(trim(fgets(STDIN)));

$result = viralAdvertising($n);

fwrite($fptr, $result . "\n");

fclose($fptr);

```
