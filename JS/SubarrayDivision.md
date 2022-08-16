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
 * Complete the 'birthday' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER_ARRAY s
 *  2. INTEGER d
 *  3. INTEGER m
 */

function birthday(s, d, m) {
    // Write your code here
    let countRight = 0;
    let totalS = parseInt(s.length);
    for(let i=0;i<m;i++){
        let countD = 0;
        let countM = 0;
        for(let k=0; k<totalS; k++){
            if(k<i){
                continue;
            }
            countD += s[k];
            countM++;
            if(countM === m){
                if(countD === d){
                    countRight++;
                }
                countD = 0;
                countM = 0;
            }
        }
    }    
    return countRight;
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const n = parseInt(readLine().trim(), 10);

    const s = readLine().replace(/\s+$/g, '').split(' ').map(sTemp => parseInt(sTemp, 10));

    const firstMultipleInput = readLine().replace(/\s+$/g, '').split(' ');

    const d = parseInt(firstMultipleInput[0], 10);

    const m = parseInt(firstMultipleInput[1], 10);

    const result = birthday(s, d, m);

    ws.write(result + '\n');

    ws.end();
}


```

