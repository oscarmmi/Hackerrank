# Counting Valleys

![image](https://user-images.githubusercontent.com/23621801/185029564-ae5a8c5d-0a96-41e3-bfc8-c21856d8b34d.png)


![image](https://user-images.githubusercontent.com/23621801/185029614-d6e32568-0fa6-49ec-81e3-1e9dd9b8f60e.png)

![image](https://user-images.githubusercontent.com/23621801/185029654-d4baa49a-6794-42e1-b783-41e6d63c0ec2.png)


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
 * Complete the 'countingValleys' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts following parameters:
 *  1. INTEGER steps
 *  2. STRING path
 */

function countingValleys(steps, path) {
    // Write your code here
    let aSteps = path.split('');
    let counter = 0;
    let valleyCounter = 0;
    let flagValley = 0;
    aSteps.forEach(function(item){
        if(item.toUpperCase() == 'D'){
            counter--;
        }else if(item.toUpperCase() == 'U'){
            counter++;
        }
        if(!flagValley && counter<0){
            valleyCounter++;
            flagValley = 1;
        }
        if(flagValley && counter>=0){
            flagValley = 0;
        }
    });
    return valleyCounter;
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const steps = parseInt(readLine().trim(), 10);

    const path = readLine();

    const result = countingValleys(steps, path);

    ws.write(result + '\n');

    ws.end();
}


```
