# Birthday cake Candles 

You are in charge of the cake for a child's birthday. You have decided the cake will have one candle for each year of their total age. 
They will only be able to blow out the tallest of the candles. Count how many candles are tallest.


### Example

candles = [4, 4, 1, 3]


The maximum height candles are  units high. There are 2 of them, so return 2.


### Function Description


Complete the function birthdayCakeCandles in the editor below.

birthdayCakeCandles has the following parameter(s):

* int candles[n]: the candle heights

### Returns

* int: the number of candles that are tallest

### Input Format

The first line contains a single integer, n , the size of candles[].
The second line contains n space-separated integers, where each integer i describes the height of candles[i].

### Constraints

* 1 <= n <= 10^5 
* 1 <= candles[i] <= 10^7

### Sample Input 0

![image](https://user-images.githubusercontent.com/23621801/179852947-f68ff1ed-0f38-455a-98c8-6f1d2fe7f9bd.png)

### Sample Output 0

![image](https://user-images.githubusercontent.com/23621801/179853010-e59c526b-d572-48f3-ade3-0bc2488c14a6.png)

### Explanation 0

Candle heights are [3, 2, 1, 3]. The tallest candles are 3 units, and there are 2 of them.

```php

<?php

/*
 * Complete the 'birthdayCakeCandles' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER_ARRAY candles as parameter.
 */

function birthdayCakeCandles($candles) {
    // Write your code here
    /*
    candles.sort(function(a, b) {
        return a - b;
    });
    let counterMax = 0;
    let max = candles[(candles.length - 1)];
    candles.forEach(function(item){
        if(max === item){
            counterMax++;
        }
    });
    return counterMax;
    */
    sort($candles);
    $max = $candles[(count($candles) - 1)];
    $counter = 0;
    foreach($candles as $candle){
        if($max === $candle){
            $counter++;
        }
    }
    return $counter;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$candles_count = intval(trim(fgets(STDIN)));

$candles_temp = rtrim(fgets(STDIN));

$candles = array_map('intval', preg_split('/ /', $candles_temp, -1, PREG_SPLIT_NO_EMPTY));

$result = birthdayCakeCandles($candles);

fwrite($fptr, $result . "\n");

fclose($fptr);

```
