### Numbers, strings
- [x] 7 kyu https://www.codewars.com/kata/highest-and-lowest
```
function highAndLow(numbers){
  return ( Math.max(...numbers.split(' ')) + " " + Math.min(...numbers.split(' ')));
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
- [x] 6 kyu https://www.codewars.com/kata/multiples-of-3-or-5
```
function solution(number){ 
  console.log(number);
  if(number < 3){
    return 0;
  }
  let arr = [];
  let count = 0;
  while(count < number){
    if((count%3) === 0 || (count%5) === 0){
      arr.push(count);
    }
    count++;
  }
  if(arr.length === 1){
    return arr[0];
  }else{
    return arr.reduce((a,b)=>{
    return a+b;
  })
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
- [] 6 kyu https://www.codewars.com/kata/nuclear-missile-manager
- [] 6 kyu https://www.codewars.com/kata/closures-and-scopes
- [] 6 kyu https://www.codewars.com/kata/can-you-keep-a-secret
### Date
- [] 7 kyu https://www.codewars.com/kata/the-coupon-code
- [] 7 kyu https://www.codewars.com/kata/unlucky-days
- [] 4 kyu https://www.codewars.com/kata/human-readable-duration-format
### Objects
- [] 7 kyu https://www.codewars.com/kata/my-language-skills
- [] 6 kyu https://www.codewars.com/kata/run-length-encoding
- [] 6 kyu https://www.codewars.com/kata/lets-recycle