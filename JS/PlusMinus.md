# Plus Minus

Given an array of integers, calculate the ratios of its elements that are positive, negative, and zero. 
Print the decimal value of each fraction on a new line with 6 places after the decimal.


### Note: 
This challenge introduces precision problems. The test cases are scaled to six decimal places, though answers with absolute error of up to 10^-4 are acceptable.

### Example

arr = [1, 1, 0, -1, -1]

There are n = 5 elements, two positive, two negative and one zero. Their ratios are 2 / 5 = 0.400000 , 2 / 5 = 0.400000 and 1 / 5 = 0.200000. Results are printed as:

![image](https://user-images.githubusercontent.com/23621801/179796933-373b1b7d-b9d2-4ad4-81e4-3b35f489fd64.png)

### Function Description

Complete the plusMinus function in the editor below.

plusMinus has the following parameter(s):

* int arr[n]: an array of integers

### Print

Print the ratios of positive, negative and zero values in the array. Each value should be printed on a separate line with 6  digits after the decimal. 
The function should not return a value.

### Input Format

The first line contains an integer, n , the size of the array.
The second line contains n space-separated integers that describe arr[n].

### Constraints


0 < n <= 100
-100 <= arr[i] <= 100


Print the following 3 lines, each to 6 decimals:


1. proportion of positive values
2. proportion of negative values
3. proportion of zeros


## Sample Input

![image](https://user-images.githubusercontent.com/23621801/179798366-6bd20d63-5207-414f-b135-fe1e7f234dbc.png)


## Sample Output

![image](https://user-images.githubusercontent.com/23621801/179798961-f8cb50c7-4d71-468b-9b51-a2963138f9cc.png)


## Explanation


There are 3 positive numbers, 2 negative numbers, and  1 zero in the array.
The proportions of occurrence are positive: 3 / 6 = 0.500000, negative: 2 / 6 = 0.3333333 and zeros: 1 / 6 = 0.1666667




```js

'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'plusMinus' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function plusMinus(arr) {
    // Write your code here
    let positives = 0;
    let negatives = 0;
    let zeros = 0;
    let total = parseInt(arr.length);
    arr.forEach(function(item){
        if(item > 0){
            positives++;
        }else if(item < 0){
            negatives++;
        }else{
            zeros++;
        }
    });
    let resultPositives = '0.000000';
    let resultNegatives = '0.000000';
    let resultZeros = '0.000000';
    if(total > 0){
        resultPositives =  Math.round((positives / total) * 1000000) / 1000000;    
        let aRPositive = ('' + resultPositives).split('.');
        if(aRPositive.length>1){
            resultPositives = aRPositive[0]+ '.' +aRPositive[1].padEnd(6,'0');
        }else{
            resultPositives = aRPositive[0]+ '.' + ''.padEnd(6,'0');
        }
        resultNegatives = Math.round((negatives / total) * 1000000) / 1000000;
        let aRNegatives = ('' + resultNegatives).split('.');
        if(aRNegatives.length>1){
            resultNegatives = aRNegatives[0]+ '.' +aRNegatives[1].padEnd(6,'0');
        }else{
            resultNegatives = aRNegatives[0]+ '.' + ''.padEnd(6,'0');
        }
        resultZeros = Math.round((zeros / total) * 1000000) / 1000000;
        let aRZeros = ('' + resultZeros).split('.');
        if(aRZeros.length>1){
            resultZeros = aRZeros[0]+ '.' +aRZeros[1].padEnd(6,'0');
        }else{
            resultZeros = aRZeros[0]+ '.' + ''.padEnd(6,'0');
        }
    }
    console.log(resultPositives);
    console.log(resultNegatives);
    console.log(resultZeros);
}

function main() {
    const n = parseInt(readLine().trim(), 10);

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    plusMinus(arr);
}




```
