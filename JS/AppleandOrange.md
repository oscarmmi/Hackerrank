# Apple and Orange

Sam's house has an apple tree and an orange tree that yield an abundance of fruit. Using the information given below, determine the number of apples and oranges that land on Sam's house.

In the diagram below:

* The red region denotes the house, where s is the start point, and t is the endpoint. The apple tree is to the left of the house, and the orange tree is to its right.

* Assume the trees are located on a single point, where the apple tree is at point a, and the orange tree is at point b.

* When a fruit falls from its tree, it lands d units of distance from its tree of origin along the x-axis. *A negative value of d means the fruit fell d units to the tree's left, and a positive value of d means it falls d units to the tree's right. *

![image](https://user-images.githubusercontent.com/23621801/182965335-7a144725-be24-4d07-ada2-49cb6f244248.png)

![image](https://user-images.githubusercontent.com/23621801/182965466-ec572436-d60b-4ab1-b2fd-2876223183fa.png)


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
 * Complete the 'countApplesAndOranges' function below.
 *
 * The function accepts following parameters:
 *  1. INTEGER s
 *  2. INTEGER t
 *  3. INTEGER a
 *  4. INTEGER b
 *  5. INTEGER_ARRAY apples
 *  6. INTEGER_ARRAY oranges
 */

function countApplesAndOranges(s, t, a, b, apples, oranges) {
    // Write your code here
    let numApples = parseInt(apples.length);
    let inHouseApples = 0;
    let inHouseOranges = 0;
    let realPositionApple = 0;
    let realPositionOrange = 0;
    for(let i=0; i<numApples; i++){
        realPositionApple = a + apples[i];
        if(realPositionApple>=s && realPositionApple<=t){
            inHouseApples++;
        }
    }
    let numOranges = parseInt(oranges.length);
    for(let i=0; i<numOranges; i++){
        realPositionOrange = b + oranges[i];
        if(realPositionOrange>=s && realPositionOrange<=t){
            inHouseOranges++;
        }
    }
    console.log(inHouseApples);
    console.log(inHouseOranges);
}

function main() {
    const firstMultipleInput = readLine().replace(/\s+$/g, '').split(' ');

    const s = parseInt(firstMultipleInput[0], 10);

    const t = parseInt(firstMultipleInput[1], 10);

    const secondMultipleInput = readLine().replace(/\s+$/g, '').split(' ');

    const a = parseInt(secondMultipleInput[0], 10);

    const b = parseInt(secondMultipleInput[1], 10);

    const thirdMultipleInput = readLine().replace(/\s+$/g, '').split(' ');

    const m = parseInt(thirdMultipleInput[0], 10);

    const n = parseInt(thirdMultipleInput[1], 10);

    const apples = readLine().replace(/\s+$/g, '').split(' ').map(applesTemp => parseInt(applesTemp, 10));

    const oranges = readLine().replace(/\s+$/g, '').split(' ').map(orangesTemp => parseInt(orangesTemp, 10));

    countApplesAndOranges(s, t, a, b, apples, oranges);
}


```
