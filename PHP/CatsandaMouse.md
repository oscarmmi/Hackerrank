# Cats and a Mouse

![image](https://user-images.githubusercontent.com/23621801/186786034-95b92e9b-4655-4d85-8278-739d78cad3c3.png)

![image](https://user-images.githubusercontent.com/23621801/186786083-6379e095-c414-4875-ad63-afb75e7e801a.png)

![image](https://user-images.githubusercontent.com/23621801/186786126-2a8d230d-4ef7-4879-9c63-f2c05bd9e254.png)

```php

<?php

// Complete the catAndMouse function below.
function catAndMouse($x, $y, $z) {
    $aToMouse = abs($x - $z);
    $bToMouse = abs($y - $z);
    if($aToMouse < $bToMouse){
        return 'Cat A';
    }else if($bToMouse < $aToMouse){
        return 'Cat B';
    }
    return 'Mouse C';
}

$fptr = fopen(getenv("OUTPUT_PATH"), "w");

$stdin = fopen("php://stdin", "r");

fscanf($stdin, "%d\n", $q);

for ($q_itr = 0; $q_itr < $q; $q_itr++) {
    fscanf($stdin, "%[^\n]", $xyz_temp);
    $xyz = explode(' ', $xyz_temp);

    $x = intval($xyz[0]);

    $y = intval($xyz[1]);

    $z = intval($xyz[2]);

    $result = catAndMouse($x, $y, $z);

    fwrite($fptr, $result . "\n");
}

fclose($stdin);
fclose($fptr);


```
