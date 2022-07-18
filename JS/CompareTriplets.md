# Compare Triplets

Alice and Bob each created one problem for HackerRank. A reviewer rates the two challenges, awarding points on a scale from 1 to 100 for three categories: problem clarity, originality, and difficulty.

The rating for Alice's challenge is the triplet a = (a[0], a[1], a[2]), and the rating for Bob's challenge is the triplet b = (b[0], b[1], b[2]).

The task is to find their comparison points by comparing a[0] with b[0], a[1] with b[1], and a[2] with b[2].

* If a[i] > b[i], then Alice is awarded 1 point.
* If a[i] < b[i], then Bob is awarded 1 point.
* If a[i] = b[i], then neither person receives a point.


Comparison points is the total points a person earned.

Given a and b, determine their respective comparison points.

### Example

a = [1, 2, 3]

b = [3, 2, 1]

* For elements *0*, Bob is awarded a point because a[0].

* For the equal elements a[1] and b[1], no points are earned.

* Finally, for elements 2, a[2] > b[2] so Alice receives a point.

The return array is [1, 1] with Alice's score first and Bob's second.

## Function Description

Complete the function compareTriplets in the editor below.

compareTriplets has the following parameter(s):

* int a[3]: Alice's challenge rating

* int b[3]: Bob's challenge rating

## Return

* int[2]: Alice's score is in the first position, and Bob's score is in the second.

## Input Format

The first line contains 3 space-separated integers, a[0], a[1], and a[2], the respective values in triplet a.
The second line contains 3 space-separated integers, b[0], b[1], and b[2], the respective values in triplet b.

## Constraints

* 1 ≤ a[i] ≤ 100
* 1 ≤ b[i] ≤ 100

## Sample Input 0

![image](https://user-images.githubusercontent.com/23621801/179627129-1e6eda45-b586-4139-af88-acb40fe893be.png)


## Sample Output 0

![image](https://user-images.githubusercontent.com/23621801/179627193-4307b122-e843-411d-aa49-db18ae87faac.png)


## Explanation 0

In this example:

![image](https://user-images.githubusercontent.com/23621801/179627388-cb344fea-7d8f-4d09-92d8-c4103deda966.png)


Now, let's compare each individual score:


![image](https://user-images.githubusercontent.com/23621801/179627576-86809277-46bc-42f1-b147-4c334da48dcf.png)


Alice's comparison score is 1, and Bob's comparison score is 1. Thus, we return the array [1, 1].



## Sample Input 1

![image](https://user-images.githubusercontent.com/23621801/179627700-8d16112f-b383-443f-8cbc-f568c545d86c.png)


## Sample Output 1

![image](https://user-images.githubusercontent.com/23621801/179627750-2b554759-32af-4dda-806b-0f0ef502ba45.png)


## Explanation 1

![image](https://user-images.githubusercontent.com/23621801/179627798-8dc75387-4ad4-4e9c-87db-f558e042a7a5.png)




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
 * Complete the 'compareTriplets' function below.
 *
 * The function is expected to return an INTEGER_ARRAY.
 * The function accepts following parameters:
 *  1. INTEGER_ARRAY a
 *  2. INTEGER_ARRAY b
 */

function compareTriplets(a, b) {
    // Write your code here
    let results = [0, 0];
    for(let i=0;i<3;i++){
        if(a[i]>b[i]){
            results[0]++;
        }else if(a[i]<b[i]){
            results[1]++;
        }
    }
    return results;
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const a = readLine().replace(/\s+$/g, '').split(' ').map(aTemp => parseInt(aTemp, 10));

    const b = readLine().replace(/\s+$/g, '').split(' ').map(bTemp => parseInt(bTemp, 10));

    const result = compareTriplets(a, b);

    ws.write(result.join(' ') + '\n');

    ws.end();
}


```

