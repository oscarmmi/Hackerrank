# Migratory Birds

Given an array of bird sightings where every element represents a bird type id, determine the id of the most frequently sighted type. If more than 1 type has been spotted that maximum amount, return the smallest of their ids.

### Example

![image](https://user-images.githubusercontent.com/23621801/184927666-e9c86021-1d39-447d-b11a-1c59cd815f88.png)

### Function Description

Complete the migratoryBirds function in the editor below.

migratoryBirds has the following parameter(s):

* int arr[n]: the types of birds sighted

### Returns

* int: the lowest type id of the most frequently sighted birds


### Input Format

The first line contains an integer,n , the size of arr.
The second line describes arr as n space-separated integers, each a type number of the bird sighted.

### Constraints

![image](https://user-images.githubusercontent.com/23621801/184927960-0d4fdedf-763f-4ea9-8b0c-7dc4d0398b30.png)

### Sample Input 0

![image](https://user-images.githubusercontent.com/23621801/184928022-4cb77b47-f0f5-41fe-aeb4-fee2d21b253f.png)


### Sample Output 0


![image](https://user-images.githubusercontent.com/23621801/184928068-45b3dd84-23ab-41f6-b620-e6dcf75b4f9e.png)


### Explanation 0

![image](https://user-images.githubusercontent.com/23621801/184928142-5b18fad2-c11b-4378-81e9-c3e032763866.png)




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
 * Complete the 'migratoryBirds' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function migratoryBirds(arr) {
    // Write your code here
    let aIds = [];
    let aCounter = [];
    let max = -1;
    let currentValue = 0;
    arr.forEach(function (item){
        let index = aIds.indexOf(item);
        if(index>-1){
            aCounter[index]++;
            currentValue = aCounter[index];
        }else{
            aIds.push(item);
            aCounter.push(0);
        }
        if(currentValue > max){
            max = currentValue;
        }
    });
    let aMax = [];
    aCounter.forEach(function (item, index){
        if(max == item){
            aMax.push(aIds[index]);
        }
    });
    if(aMax.length == 1){
        return aMax[0];
    }
    aMax.sort(function(a, b) {
        return a - b;
    });
    return aMax[0];
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const arrCount = parseInt(readLine().trim(), 10);

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    const result = migratoryBirds(arr);

    ws.write(result + '\n');

    ws.end();
}


```
