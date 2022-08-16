# Bill Division

Two friends Anna and Brian, are deciding how to split the bill at a dinner. Each will only pay for the items they consume. Brian gets the check and calculates Anna's portion. You must determine if his calculation is correct.

![image](https://user-images.githubusercontent.com/23621801/184953539-b311b02b-6a2c-4628-869e-f133a2afd2f1.png)

### Function Description

Complete the bonAppetit function in the editor below. It should print Bon Appetit if the bill is fairly split. Otherwise, it should print the integer amount of money that Brian owes Anna.

bonAppetit has the following parameter(s):

* bill: an array of integers representing the cost of each item ordered
* k: an integer representing the zero-based index of the item Anna doesn't eat
* b: the amount of money that Anna contributed to the bill

The first line contains two space-separated integers n and k, the number of items ordered and the 0-based index of the item that Anna did not eat.
The second line contains n space-separated integers bill[i] where 0 <= i < n.
The third line contains an integer, b, the amount of money that Brian charged Anna for her share of the bill.


### Constraints

![image](https://user-images.githubusercontent.com/23621801/184953893-e8e0ecfd-94e0-4622-8e52-e716c50424c0.png)


![image](https://user-images.githubusercontent.com/23621801/184953931-b64d2d6c-5a83-4010-be6e-86878201c2cf.png)

![image](https://user-images.githubusercontent.com/23621801/184953977-33ffda0f-8713-44b7-8198-65bd0f382696.png)


```php

<?php

/*
 * Complete the 'bonAppetit' function below.
 *
 * The function accepts following parameters:
 *  1. INTEGER_ARRAY bill
 *  2. INTEGER k
 *  3. INTEGER b
 */

function bonAppetit($bill, $k, $b) {
    // Write your code here
    $calculatedBill = 0;
    foreach($bill as $key => $item){
        if($key === $k){
            continue;
        }
        $calculatedBill += $item;
    }
    $calculatedBill = $calculatedBill / 2;
    if($calculatedBill === $b){
        print "Bon Appetit";
    }else{
        print ($b - $calculatedBill);
    }
}

$first_multiple_input = explode(' ', rtrim(fgets(STDIN)));

$n = intval($first_multiple_input[0]);

$k = intval($first_multiple_input[1]);

$bill_temp = rtrim(fgets(STDIN));

$bill = array_map('intval', preg_split('/ /', $bill_temp, -1, PREG_SPLIT_NO_EMPTY));

$b = intval(trim(fgets(STDIN)));

bonAppetit($bill, $k, $b);


```
