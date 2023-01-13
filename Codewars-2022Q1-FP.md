- [x] 7 kyu https://www.codewars.com/kata/first-class-function-factory
```
function factory(x){
    return function(arr) {
        return arr.map( e => e*x );
    }
}
```
- [] 7 kyu https://www.codewars.com/kata/the-wheat-slash-rice-and-chessboard-problem
```
function squaresNeeded(grains){
  //your code here
  let square = 0;
  while(2 ** square - 1 < grains) {
    square++;
  }
  
  return square;
}
```
- [x] 6 kyu https://www.codewars.com/kata/function-composition
```
function compose(f,g) {
  // Compose the two functions here!
      return function (...x) {
        return f(g(...x));
    }
}
```
- [x] 6 kyu https://www.codewars.com/kata/function-composition-1
```
function compose(...arg) {
  // Your solution
    return function (x) {
        return arg.reduceRight((acc, f) => f(acc), x);
    }
}
```
- [x] 6 kyu https://www.codewars.com/kata/reusable-memoisation
```
function memo(fn) {
    let res = {};
    return function(arg) {
        let param = typeof arg !== 'object' ? arg : JSON.stringify(arg);
        if (param in res) {
            return res[param];
        }
        res[param] = fn(arg);
        return res[param];
    };
}
```
- [x] 6 kyu https://www.codewars.com/kata/mutual-recursion
```
function F(n) {
    if(n === 0) {
        return 1;
    }
    return n - M(F(n - 1));
}
  
function M(n) {
    if(n === 0) {
        return 0;
    }
    return n - F(M(n - 1));
}
```
- [x] 6 kyu https://www.codewars.com/kata/once
```
function once(fn) {
  let ctrl = false;
  return function (...x) {
    console.log(...x);
    if (!ctrl) {
      ctrl = true;
      return fn(...x);
    }
    return undefined;
  }
}
```
- [x] 6 kyu https://www.codewars.com/kata/multifilter
```
var multiFilter = function(...fn){
    if (fn.length === 0) return (x)=> x;
	return function(x){
    console.log(x);
        if ([...fn].every(f => f(x))) {
            return x;
        }
    }; // change it for your code
};
```
- [x] 6 kyu https://www.codewars.com/kata/combinator-flip
```
function flip(fn) {
    //complete this function here
  return function(...arg) {
    console.log(arg);
    let newArg = arg.reverse();
    return fn(...newArg);
  }
}
```
- [x] 5 kyu https://www.codewars.com/kata/function-cache
```
function cache(func) {
  // do your magic here
  let args = {};
  return function (...arg) {
    let param = JSON.stringify(arg);
    if (param in args) {
      return args[param];
    }
    args[param] = func(...arg);
    return args[param];
  }
}
```
- [x] 5 kyu https://www.codewars.com/kata/a-chain-adding-function
```
function add(n) {
  let res = n;
  function ret(m) {
    return add(n + m);
  }
  ret.toString = function(){
    return res;
  };
  return ret;
}
```
- [x] 5 kyu https://www.codewars.com/kata/lazy-repeater
```
function makeLooper(str) {
  // TODO: return a function that loops through 'str' on successive invocations
  let arr = [...str];
  let index = 0;
  return function () {
    let letter = arr[index];
    if (index < arr.length - 1) {
      index++;
    } else {
      index = 0;
    }
    return letter;
  }
}
```
- [x] 4 kyu https://www.codewars.com/kata/currying-vs-partial-application
```
function curryPartial(fn, ...args) {
  if (fn.length <= args.length) return fn(...args);
  return  function (...arg) {
    let x = curryPartial(fn, ...args, ...arg);
    return x;    
  }
}
```