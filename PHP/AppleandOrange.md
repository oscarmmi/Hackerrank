# Apple and Orange

Sam's house has an apple tree and an orange tree that yield an abundance of fruit. Using the information given below, determine the number of apples and oranges that land on Sam's house.

In the diagram below:

* The red region denotes the house, where s is the start point, and t is the endpoint. The apple tree is to the left of the house, and the orange tree is to its right.

* Assume the trees are located on a single point, where the apple tree is at point a, and the orange tree is at point b.

* When a fruit falls from its tree, it lands d units of distance from its tree of origin along the x-axis. *A negative value of d means the fruit fell d units to the tree's left, and a positive value of d means it falls d units to the tree's right. *

![image](https://user-images.githubusercontent.com/23621801/182965335-7a144725-be24-4d07-ada2-49cb6f244248.png)

![image](https://user-images.githubusercontent.com/23621801/182965466-ec572436-d60b-4ab1-b2fd-2876223183fa.png)


```php

<?php

/*
 * Complete the 'countApplesAndOranges' function below.
 *
 * The function accepts following parameters:
 *  1. INTEGER s
 *  2. INTEGER t
 *  3. INTEGER a
 *  4. INTEGER b
 *  5. INTEGER_ARRAY apples
 *  6. INTEGER_ARRAY oranges
 */

function countApplesAndOranges($s, $t, $a, $b, $apples, $oranges) {
    // Write your code here
    $inHouseApples = 0;
    $inHouseOrange = 0;
    foreach($apples as $apple){
        $realPositionApple = $apple + $a;        
        if($realPositionApple>=$s && $realPositionApple<=$t){
            $inHouseApples++;
        }
    }
    foreach($oranges as $orange){
        $realPositionOrange = $orange + $b;
        if($realPositionOrange>=$s && $realPositionOrange<=$t){
            $inHouseOrange++;
        }
    }
    print $inHouseApples."\n";
    print $inHouseOrange;
}

$first_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$s = intval($first_multiple_input[0]);

$t = intval($first_multiple_input[1]);

$second_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$a = intval($second_multiple_input[0]);

$b = intval($second_multiple_input[1]);

$third_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$m = intval($third_multiple_input[0]);

$n = intval($third_multiple_input[1]);

$apples_temp = rtrim(fgets(STDIN));

$apples = array_map('intval', preg_split('/ /', $apples_temp, -1, PREG_SPLIT_NO_EMPTY));

$oranges_temp = rtrim(fgets(STDIN));

$oranges = array_map('intval', preg_split('/ /', $oranges_temp, -1, PREG_SPLIT_NO_EMPTY));

countApplesAndOranges($s, $t, $a, $b, $apples, $oranges);


```
