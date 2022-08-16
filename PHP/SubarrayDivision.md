# Subarray Division

Two children, Lily and Ron, want to share a chocolate bar. Each of the squares has an integer on it.

Lily decides to share a contiguous segment of the bar selected such that:

* The length of the segment matches Ron's birth month, and,
* The sum of the integers on the squares is equal to his birth day.

Determine how many ways she can divide the chocolate.

### Example

![image](https://user-images.githubusercontent.com/23621801/184796599-6fb3e981-3dbd-436f-885d-eea43fb420b3.png)


Lily wants to find segments summing to Ron's birth day, d=4 with a length equalling his birth month, m=2 . 
In this case, there are two segments meeting her criteria: [2,2] and [1,3].

### Function Description

Complete the birthday function in the editor below.

birthday has the following parameter(s):

* int s[n]: the numbers on each of the squares of chocolate
* int d: Ron's birth day
* int m: Ron's birth month

Returns

* int: the number of ways the bar can be divided


The first line contains an integer n , the number of squares in the chocolate bar.
The second line contains n space-separated integers s[i], the numbers on the chocolate squares where 0 <= i <= n.
The third line contains two space-separated integers, d and , m Ron's birth day and his birth month.


### Constraints

![image](https://user-images.githubusercontent.com/23621801/184797662-8e5aacf1-84da-4e59-975e-0fe10509716e.png)


### Sample Input 0

![image](https://user-images.githubusercontent.com/23621801/184797708-cd5a309b-014a-450b-96f5-88330807b2f5.png)


### Sample Output 0

![image](https://user-images.githubusercontent.com/23621801/184797881-da632784-a6d7-46b2-b5f6-fc845043c4b8.png)



```php

<?php

/*
 * Complete the 'birthday' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER_ARRAY s
 *  2. INTEGER d
 *  3. INTEGER m
 */

function birthday($s, $d, $m) {
    // Write your code here    
    $countRight = 0;
    for($i=0;$i<$m;$i++){
        $countD = 0;
        $countM = 0;
        foreach($s as $key => $item){
            if($key<$i){
                continue;
            }
            $countD += $item;
            $countM++;
            if($countM === $m){
                if($countD === $d){
                    $countRight++;
                }
                $countD = 0;
                $countM = 0;
            }
        }
    }    
    return $countRight;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$n = intval(trim(fgets(STDIN)));

$s_temp = rtrim(fgets(STDIN));

$s = array_map('intval', preg_split('/ /', $s_temp, -1, PREG_SPLIT_NO_EMPTY));

$first_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$d = intval($first_multiple_input[0]);

$m = intval($first_multiple_input[1]);

$result = birthday($s, $d, $m);

fwrite($fptr, $result . "\n");

fclose($fptr);


```

