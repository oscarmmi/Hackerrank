# Utopian Tree

![image](https://user-images.githubusercontent.com/23621801/186783262-19f95ba0-c226-472f-a0b2-e6ddb88f6de7.png)

![image](https://user-images.githubusercontent.com/23621801/186783366-87f5d461-e1be-4540-b55a-32c5fd932625.png)

```php

<?php

/*
 * Complete the 'utopianTree' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER n as parameter.
 */

function utopianTree($n) {
    // Write your code here
    $length = 1;
    for($i=1;$i<=$n;$i++){
        if(($i % 2)){
            $length = $length * 2;
        }else{
            $length += 1;
        }
    }
    return $length;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$t = intval(trim(fgets(STDIN)));

for ($t_itr = 0; $t_itr < $t; $t_itr++) {
    $n = intval(trim(fgets(STDIN)));

    $result = utopianTree($n);

    fwrite($fptr, $result . "\n");
}

fclose($fptr);


```
