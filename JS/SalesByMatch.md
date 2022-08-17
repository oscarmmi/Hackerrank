# Sales by Match

There is a large pile of socks that must be paired by color. Given an array of integers representing the color of each sock, determine how many pairs of socks with matching colors there are.

### Example

![image](https://user-images.githubusercontent.com/23621801/185018756-fa7ff7d4-4f5d-403c-983c-038d9f2cc2df.png)

### Function Description

Complete the sockMerchant function in the editor below.

sockMerchant has the following parameter(s):

int n: the number of socks in the pile
int ar[n]: the colors of each sock

### Returns

int: the number of pairs


### Input Format

The first line contains an integer n, the number of socks represented in arr.
The second line contains n space-separated integers, ar[i] , the colors of the socks in the pile.

### Constraints

![image](https://user-images.githubusercontent.com/23621801/185019425-a7f60b91-5e87-48bb-b42b-18c24b2f73fb.png)


### Sample Input

![image](https://user-images.githubusercontent.com/23621801/185019603-e7c9adf0-d901-4810-946f-c5434ee0cd39.png)


### Sample Output

![image](https://user-images.githubusercontent.com/23621801/185019643-8c632efd-044f-4f46-a2ee-c10d721deb03.png)

### Explanation

![image](https://user-images.githubusercontent.com/23621801/185019716-d074ad21-353d-47a6-9522-875462e1770a.png)

There are three pairs of socks.


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
 * Complete the 'sockMerchant' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER n
 *  2. INTEGER_ARRAY ar
 */

function sockMerchant(n, ar) {
    // Write your code here
    let aSockets = [];
    let counterSockets = [];
    let index = 0;
    ar.forEach(function(item){
        index = aSockets.indexOf(item);
        if(index===-1){
            aSockets.push(item);
            counterSockets.push(0);
            index = parseInt(aSockets.length) - 1;
        }
        counterSockets[index]++;
    });
    let pairCounter = 0;
    counterSockets.forEach(function(item){
        pairCounter += parseInt(item/2);
    });
    return pairCounter; 
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const n = parseInt(readLine().trim(), 10);

    const ar = readLine().replace(/\s+$/g, '').split(' ').map(arTemp => parseInt(arTemp, 10));

    const result = sockMerchant(n, ar);

    ws.write(result + '\n');

    ws.end();
}


```

