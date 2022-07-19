# Diagonal Difference 

Given a square matrix, calculate the absolute difference between the sums of its diagonals.

For example, the square matrix  is shown below:

![image](https://user-images.githubusercontent.com/23621801/179769219-eb50c61f-d558-491b-ae41-7c4485267bd2.png)

The left-to-right diagonal = 1 + 5 + 9 = 15 . The right to left diagonal = 3 + 5 + 9 = 17. Their absolute difference is | 15 - 17 | = 2.

## Function description

Complete the diagonalDifference function in the editor below.

diagonalDifference takes the following parameter:

* int arr[n][m]: an array of integers

### Return

* int: the absolute diagonal difference

### Input Format

The first line contains a single integer, n , the number of rows and columns in the square matrix arr.
Each of the next n  lines describes a row, arr[i] , and consists of n space-separated integers arr[i][j].

### Constraints

* -100 <= arr[i][j] <= 100

### Output Format

Return the absolute difference between the sums of the matrix's two diagonals as a single integer.


## Sample Input

![image](https://user-images.githubusercontent.com/23621801/179775145-b4bb70e6-ee89-4018-bad4-7513e5d0617c.png)

### Sample Output

![image](https://user-images.githubusercontent.com/23621801/179775355-24611e84-345a-4e56-bc22-93972da56094.png)


### Explanation

The primary diagonal is:

![image](https://user-images.githubusercontent.com/23621801/179775783-186da658-fa9e-4a43-9659-7b4692f781ba.png)


Sum across the primary diagonal: 11 + 5 - 12 = 4


The secondary diagonal is:


![image](https://user-images.githubusercontent.com/23621801/179778930-42fe59f2-568e-4396-925a-69178141fd3b.png)


Sum across the secondary diagonal: 4 + 5 + 10 = 19


Difference: |4 - 19| = 15

Note: |x| is the absolute value of x




```js

'use strict';

const fs = require('fs');

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
 * Complete the 'diagonalDifference' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts 2D_INTEGER_ARRAY arr as parameter.
 */

function diagonalDifference(arr) {
    // Write your code here
    let countArray = parseInt(arr.length);
    let diagonal1 = 0;
    let diagonal2 = 0;
    for(let i=0; i<countArray; i++){
        diagonal1 += parseInt(arr[i][i]);
    }
    let counter = 0;
    for(let i=(countArray - 1); i>=0; i = i - 1){
        diagonal2 += parseInt(arr[counter][i]);
        counter++;
    }
    return Math.abs(diagonal1 - diagonal2);
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const n = parseInt(readLine().trim(), 10);

    let arr = Array(n);

    for (let i = 0; i < n; i++) {
        arr[i] = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));
    }

    const result = diagonalDifference(arr);

    ws.write(result + '\n');

    ws.end();
}


```

