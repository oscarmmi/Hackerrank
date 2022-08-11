# Breaking the Records

Maria plays college basketball and wants to go pro. Each season she maintains a record of her play. She tabulates the number of times she breaks her season record for most points and least points in a game. Points scored in the first game establish her record for the season, and she begins counting from there.

### Example

scores = [10, 24, 10, 24];

Scores are in the same order as the games played. She tabulates her results as follows:

![image](https://user-images.githubusercontent.com/23621801/184253012-d30a4686-ed38-4060-aafb-5398df62708f.png)

Given the scores for a season, determine the number of times Maria breaks her records for most and least points scored during the season.

### Function Description

Complete the breakingRecords function in the editor below.

breakingRecords has the following parameter(s):

* int scores[n]: points scored per game

Returns

int[2]: An array with the numbers of times she broke her records. Index 0 is for breaking most points records, and index 1 is for breaking least points records.

### Input Format

The first line contains an integer , the number of games.
The second line contains n space-separated integers describing the respective values of ![image](https://user-images.githubusercontent.com/23621801/184253328-e7ae7b02-cd77-477e-b8b2-9c3ad1f985d5.png)


### Constraints

![image](https://user-images.githubusercontent.com/23621801/184253365-87e33af6-06c5-4dc3-a887-f699e1040a2f.png)


![image](https://user-images.githubusercontent.com/23621801/184253411-25e27c4b-010d-42ad-888a-0aa860b88006.png)



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
 * Complete the 'breakingRecords' function below.
 *
 * The function is expected to return an INTEGER_ARRAY.
 * The function accepts INTEGER_ARRAY scores as parameter.
 */

function breakingRecords(scores) {
    // Write your code here
    let counterMax = 0;
    let max = -1;
    let counterMin = 0;
    let min = 1000000000;
    scores.forEach(function(score){
        if(score < min){
            min = score;
            counterMin++;
        }
        if(score > max){
            max = score;
            counterMax++;
        }
    });
    return [(counterMax - 1), (counterMin - 1)];
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const n = parseInt(readLine().trim(), 10);

    const scores = readLine().replace(/\s+$/g, '').split(' ').map(scoresTemp => parseInt(scoresTemp, 10));

    const result = breakingRecords(scores);

    ws.write(result.join(' ') + '\n');

    ws.end();
}


```

