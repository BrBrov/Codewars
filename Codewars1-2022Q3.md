### Numbers and strings
- [x] 7 kyu https://www.codewars.com/kata/which-color-is-the-brightest
```
function brightest(colors){
    function convert(params) {
        params = params.slice(1)
        params = params.match(/\w{2}/g);
        return params.map(e => {
            return parseInt(e, 16);
        })
    }
    let rgbArr = colors.map(elem =>{
        return convert(elem);
    });
    let bright = rgbArr.map(elem=>{
        return Math.max(elem[0],elem[1],elem[2]);
    })
    let index = 0;
    let control = 0;
    bright.forEach((elem, i) => {
        if(elem > control){
            control = elem;
            index = i;
        }
    });
    return colors[index]
}
```
- [x] 7 kyu https://www.codewars.com/kata/disemvowel-trolls
```
function disemvowel(str) {
  return str.split(/[aeiou]/gi).join('');
}
```
- [x] 7 kyu https://www.codewars.com/kata/isograms
```
function isIsogram(str){
    str = str.toLowerCase();
    for (const letter of str) {
        let positions = str.search(letter);
        if (str.includes(letter, positions + 1)) {
            return false;
        }
    }
    return true;
}
```
- [x] 7 kyu https://www.codewars.com/kata/digits-explosion
```
function explode(s) {
   let arr = [];
   [...s].forEach(e=>{
   let count = e;
   while(count != 0){
        arr.push(e);
        count --;
    }
   })
  return arr.join('');
}
```
- [x] 6 kyu https://www.codewars.com/kata/handshake-problem
```
function getParticipants(handshakes){
    if(handshakes === 0){return 0;}  
    handshakes = handshakes*2;
    let d = 1 + (4*handshakes);
    let sqrtD = Math.sqrt(d);
    let x1 = (-1 - sqrtD)/2;
    let x2 = (-1 + sqrtD)/2;
    let result = (x1 > 0) ? x1 : x2;
    return Math.ceil(result + 1);
}
```
- [x] 6 kyu https://www.codewars.com/kata/duplicate-encoder
```
function duplicateEncode(word){
    let control = [];
    word = Array.from(word.toLowerCase());
    word.forEach((e,i, arr)=>{    
        if(!control.includes(i)){
        control.push(i);
        if(arr.includes(e, i + 1)){
            arr.forEach((elem, index, a)=>{
                if(elem === e){
                    control.push(index);
                    a[index] = ')';
                }
            })
        }else{
            arr[i] = '(';
        }
        }
    })
   return word.join('');
}
```
- [x] 6 kyu https://www.codewars.com/kata/n-th-fibonacci
```
function nthFibo(n) {
  let sequence = [0,1];
  if(n == 1){
    return 0;
  }else if(n == 2){
    return 1;
  }else{
    let count = 1;
    while(count !== (n-1)){
      sequence.push((sequence[count] + (sequence[count - 1])));
      count ++;
    }
    return sequence[count];
  }
}
```
- [x] 4 kyu https://www.codewars.com/kata/human-readable-duration-format
```
function formatDuration (seconds) {
    console.log(seconds)
    let stringReference = {
        year: 'year',
        day: 'day',
        hour: 'hour',
        minute: 'minute',
        second: 'second',
        now: 'now'
    }
    if (seconds === 0) {
        return stringReference.now;
    }
    let time = {};
    if (seconds < 60) {
        time.second = seconds;
    } else {
        time.second = seconds % 60;
        let minute = (seconds - time.second) / 60;
        if (minute < 60) {
            time.minute = minute;
        } else {
            time.minute = minute % 60;
            let hour = (minute - time.minute) / 60;
            if (hour < 24) {
                time.hour = hour;
            } else {
                time.hour = hour % 24;
                let day = (hour - time.hour) / 24;
                if (day < 365) {
                    time.day = day;
                } else {
                    time.day = day % 365;
                    time.year = (day - time.day) / 365;
                }
            }
        }
    }
    let result = [];
    for (const key in time) {
        if (time[key] !== 0) {
            if (time[key] === 1) {
                result.push(`${time[key]} ${stringReference[key]}`);
            } else {
                result.push(`${time[key]} ${stringReference[key]}s`);
            }
        }

    }
    result.reverse();
    if(result.length === 1){
        return result.join('');
    }else if(result.length === 2){
        let [left, right] = result;
        result = [];
        result.push(left);
        result.push(` and `);
        result.push(right);
        return result.join('');
    }else{
        let timeBackUp = [];
        timeBackUp.push(result.pop());
        timeBackUp.push(' and ');
        timeBackUp.push(result.pop());
        result = result.map(e=>{
            return e + `, `;
        })
        result = result.join('');
        timeBackUp.reverse();
        return result + timeBackUp.join('');
    }
}
```
### Arrays
- [x] 7 kyu https://www.codewars.com/kata/head-tail-init-and-last
```
let head = (arr) =>{
  console.log('head ' + arr);
  if(arr.length === 0){
    return undefined;
  }
  return arr[0];
}
let tail = (arr) =>{
  return arr.slice(1);
}
let init = (arr) =>{
  return arr.slice(0, (arr.length - 1));
}
let last = (arr) =>{
  console.log('last ' + arr);
  if(arr.length === 0){
    return undefined;
  }
  return arr[arr.length - 1];
}
```
- [x] 6 kyu https://www.codewars.com/kata/array-deep-count
```
function deepCount(a){
  let count = 0;
  function getCount(arr){
    count = count + arr.length;
    arr.forEach(e=>{
      if(typeof e === 'object'){
        return getCount(e);
      }
    })
  }
  getCount(a);
  return count;
}
```
- [x] 6 kyu https://www.codewars.com/kata/length-of-missing-array
```
function getLengthOfMissingArray(arr) {
  console.log(arr);
  if(arr === null || arr.length === 0 || !arr){
    return 0;    
  }
  let countArr = [];
  for (const item of arr) {
    console.log(Array.isArray(item));
    if(Array.isArray(item) === false|| item.length === 0){
     return 0;
    }else{
        countArr.push(item.length);
    }
  }
  countArr.sort((a,b)=>{
     return a - b;
  })

  for (let index = 0; index < countArr.length; index++) {
    if(countArr[index] + 1 !== countArr[index + 1]){
      return countArr[index] + 1;      
    }
  }
}
```
- [x] 6 kyu https://www.codewars.com/kata/pair-of-gloves
```
function numberOfPairs(gloves){
  console.log(gloves);
  let stack = [].concat(gloves);
  stack.sort();
  let count = 0;  
  while(stack.length > 1){
    let x = stack.pop();
    if(x === stack[stack.length - 1]){
        count ++;
        stack.pop();
    }
  }
  return count;
}
```
- [x] 6 kyu https://www.codewars.com/kata/sorting-by-bits
```
function sortByBit(arr) {
    let convert = (num) =>{
      let x = num.toString(2);
      x = [...x].reduce((a,b)=>{
           return +a - (-b);
      })
      return Number(x);
    }

    return arr.sort((curr, next)=>{
      let binCurr = convert(curr);
      let binNext = convert(next);
      if(binCurr > binNext){
        return 1;
      }else if(binCurr === binNext){
        if(curr > next){
            return 1;
        }else{
            return -1;
        }
      }else{
        return -1;
      }
    });
}
```
- [x] 6 kyu https://www.codewars.com/kata/lets-recycle
```
function recycle(array) {
    let arrayOfBox = {
        paper: [],
        glass: [],
        organic: [],
        plastic: []
    };

    array.forEach(e=>{
        arrayOfBox[`${e.material}`].push(e.type);
        if(e.hasOwnProperty('secondMaterial')){
            arrayOfBox[`${e.secondMaterial}`].push(e.type);
        }
    })
    return [arrayOfBox.paper, arrayOfBox.glass, arrayOfBox.organic, arrayOfBox.plastic];
}
```
### Functions
- [x] 7 kyu https://www.codewars.com/kata/javascript-mathematician
```
function calculate(...a) {
    a = a.reduce((x,y)=>{
        return x + y;
    })
    return function(...b){
        b = b.reduce((x,y)=>{
            return x + y;
        })
        return a + b;
    }
}
```
- [x] 6 kyu https://www.codewars.com/kata/javascript-from-the-inside-number-1-map
```
let maps = function (callback, thisArg){
    let arr = new Array();
    arr = arr.concat(this);
    if(Array.isArray(thisArg)){
        callback = callback.bind(thisArg);
    }
    let index = 0; 
    while(index < this.length){
        if(index in this){
           arr[index] = callback(arr[index], index, this);
        }
        index++;
    }
    return arr;
}

Array.prototype.map = maps;
```
- [x] 6 kyu https://www.codewars.com/kata/javascript-from-the-inside-number-2-filter
```
Array.prototype.filter = function (callback, thisArg){
    let arr = [].concat(this);
    console.log('this input -> ' + arr);
    let lengthArr = arr.length;
    if(Array.isArray(thisArg) || (typeof thisArg) === "number"){
        callback = callback.bind(thisArg);
    }
    let index = 0;
    let output = [];
    while(index < lengthArr){
        if(index in arr){
            if(arr[index]){
              let control = (callback(arr[index], index, arr)) ? arr[index] : false;
              if(control){
                  output.push(control);
              }
            }else{
                output.push(arr[index]);
            }
          }
        index++;
    }
    return output;
}
```
- [x] 6 kyu https://www.codewars.com/kata/power-bind
```
Function.prototype.bind = function (ctx) {    
    let f = this;
    Object.assign(global, ctx);
    return function () {      
      return f();
    }
};

let func = function () {
    return this.prop;
};
```
- [x] 6 kyu https://www.codewars.com/kata/closures-and-scopes
```
function createFunctions(n) {
    var callbacks = [];
    for (let i = 0; i < n; i++) {
        callbacks.push(function () {

            return i;
        });
    }

    return callbacks;
}
```
- [x] 6 kyu https://www.codewars.com/kata/can-you-keep-a-secret
```
function createSecretHolder(secret) {
    let obj = {};
    Object.defineProperty(obj, '_secret', {
        enumerable: false,
        writable: false,
        configurable: true
    })
    Object.defineProperty(obj, 'get', {
        get: function () {
            return this._secret;
        }
    })
    Object.defineProperty(obj, 'set', {
        set: function (secret) {
            Object.defineProperty(this, '_secret', {
                value: secret,
                enumerable: false,
                writable: false,
                configurable: true
            })
        }
    })
    obj.getSecret = function () {
        return this.get;
    }
    obj.setSecret = function (params) {
        this.set = params;
    }
    obj.setSecret(secret);
    return obj;
}
```
### Date and time
- [x] 7 kyu https://www.codewars.com/kata/the-coupon-code
```
function checkCoupon(enteredCode, correctCode, currentDate, expirationDate){
  console.log(`code: ${enteredCode}, correctCode: ${correctCode}, date: ${currentDate}, expDate: ${expirationDate}`);
    if(enteredCode === correctCode){
      let cDate = new Date(currentDate);
      let eDate = new Date(expirationDate);
      if(cDate <= eDate){
        return true;
      }else{
        return false
      }
    }else{
      return false;
    } 
}
```
- [x] 7 kyu https://www.codewars.com/kata/unlucky-days
```
function unluckyDays(year){
  console.log(year);
  let date = new Date();
  date.setFullYear(year);
  let count = 0;
  let month = 0;
  while (month < 12){
    date.setMonth(month, 13);
    if(date.getDay() === 5){
      count++;
    }
    month++;
  }
  return count;
}
```
- [x] 6 kyu https://www.codewars.com/kata/angle-between-clock-hands
```
function handAngle (date) {
  console.log(date)
  let stepAngleMinute = 6; //6 degree = 1 minute
  let stepAngleHour = 0.5;// 0,5 degree doing hour's hand for a one minute
  let oneHourAngle = 30;// from 0 to 1  = 30 degree on an analog clock
  let angleMinute = date.getMinutes() * stepAngleMinute;
  let hour = date.getHours();
  hour = (hour >=12) ? (hour = 0) : hour;
  let angleHour = hour*oneHourAngle + date.getMinutes()*stepAngleHour;
  let angle = 0;
  if(angleHour === angleMinute){
    angle = 0;
  }else if(angleMinute > angleHour){
    angle = ((angleMinute - angleHour) > 180) ? (360 - angleMinute + angleHour): (angleMinute - angleHour);
  }else{
    angle = ((angleHour - angleMinute) > 180) ? (360 - angleHour + angleMinute) : (angleHour - angleMinute);
  }
  angle = (angle * Math.PI)/180;
	return angle;
}
```
### Objects
- [x] 7 kyu https://www.codewars.com/kata/my-language-skills
```
function myLanguages(results) {
  let arr = [];
  for(const key in results){
    if(results[key] >= 60){
      let elem = [];
      elem.push(key);
      elem.push(results[key]);
      arr.push(elem);
    }
  }
  arr.sort((a,b)=>{
    return b[1] - a[1];
  })
  arr = arr.map(e=>{
    return e[0];
  })
  return arr;
}
```
- [x] 6 kyu https://www.codewars.com/kata/run-length-encoding
```
var runLengthEncoding = function(str){
  let compressed = [];
  let count = 0;
  let input  = [...str];
  for (let index = 0; index < input.length; index++) {
    count++;
    if(input[index] !== input[index + 1]){
      let coding = [];
      coding.push(count);
      coding.push(input[index]);
      compressed.push(coding);
      count = 0;
    }
  }
  return compressed // << fix this
}
```
- [x] 6 kyu https://www.codewars.com/kata/walk-the-object-path
```
function find(object, path) {
  let checkingObj = object;
  let pathOfObj = (obj, key)=>{
    if(obj.hasOwnProperty(`${key}`)){
      return obj[key];
    }else{
      return undefined;
    }
  }
  path = path.split('.');
  let output;
  for (const prop of path) {
    let result = pathOfObj(checkingObj, prop);
    if(!result){
      return undefined;
    }else if(result instanceof Object){
      checkingObj = result;
    }else{
      output = result;
    }
  }
  return output;  
}
```