# Time Conversion

Given a time in -hour AM/PM format, convert it to military (24-hour) time.

Note: - 12:00:00AM on a 12-hour clock is 00:00:00 on a 24-hour clock.
- 12:00:00PM on a 12-hour clock is 12:00:00 on a 24-hour clock.

### Example

![image](https://user-images.githubusercontent.com/23621801/179857283-683f2a9c-225b-49c6-8e7e-29a40a110fc3.png)

Return '12:01:00'.

![image](https://user-images.githubusercontent.com/23621801/179857342-bec66590-afa6-4e1c-b7b6-e21a59a5a0b3.png)

Return '00:01:00'.


## Function Description

Complete the timeConversion function in the editor below. It should return a new string representing the input time in 24 hour format.

timeConversion has the following parameter(s):

* string s: a time in  hour format

Returns

* string: the time in  hour format

### Input Format

![image](https://user-images.githubusercontent.com/23621801/179857485-69592652-363d-4b9e-9c9a-141cfe6712a6.png)


### Constraints

All input times are valid

### Sample Input 0

![image](https://user-images.githubusercontent.com/23621801/179857546-16360e34-b3b2-4c33-9c66-488e37742fad.png)

### Sample Output 0

![image](https://user-images.githubusercontent.com/23621801/179857596-34c01ed5-40e7-4e2a-9c49-6add715f68e7.png)


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
 * Complete the 'timeConversion' function below.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING s as parameter.
 */

function timeConversion(s) {
    // Write your code here
    let aS = s.split(':');
    let hour = parseInt(aS[0]);
    let type = aS[2].substring(2, 4);
    if(type.toUpperCase() === 'PM' && hour !== 12){
        hour += 12;
    }else if(type.toUpperCase() === 'AM' && hour === 12){
        hour = 0;
    }
    return ('' + hour).padStart(2, '0') + ':' + aS[1] + ':' + aS[2].replace(type, '');
}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const s = readLine();

    const result = timeConversion(s);

    ws.write(result + '\n');

    ws.end();
}


```

