# Electronics Shop

![image](https://user-images.githubusercontent.com/23621801/186786705-9fb47ed6-8e6a-4d11-84b0-6f547e663c61.png)

![image](https://user-images.githubusercontent.com/23621801/186786824-7f78aa8a-71b5-45fb-a844-de225ec3b049.png)

```php

<?php

/*
 * Complete the getMoneySpent function below.
 */
function getMoneySpent($keyboards, $drives, $b) {
    /*
     * Write your code here.
     */     
    $max = -1; 
    foreach($keyboards as $keyboard){
        foreach($drives as $drive){
            if(($drive + $keyboard) <= $b){
                if($max < ($drive + $keyboard)){
                    $max = ($drive + $keyboard);
                }        
            }
        }
    }
    return $max;
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$stdin = fopen("php://stdin", "r");

fscanf($stdin, "%[^\n]", $bnm_temp);
$bnm = explode(' ', $bnm_temp);

$b = intval($bnm[0]);

$n = intval($bnm[1]);

$m = intval($bnm[2]);

fscanf($stdin, "%[^\n]", $keyboards_temp);

$keyboards = array_map('intval', preg_split('/ /', $keyboards_temp, -1, PREG_SPLIT_NO_EMPTY));

fscanf($stdin, "%[^\n]", $drives_temp);

$drives = array_map('intval', preg_split('/ /', $drives_temp, -1, PREG_SPLIT_NO_EMPTY));

/*
 * The maximum amount of money she can spend on a keyboard and USB drive, or -1 if she can't purchase both items
 */

$moneySpent = getMoneySpent($keyboards, $drives, $b);

fwrite($fptr, $moneySpent . "\n");

fclose($stdin);
fclose($fptr);


```
