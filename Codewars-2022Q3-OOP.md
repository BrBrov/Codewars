- [x] 7 kyu https://www.codewars.com/kata/santaclausable-interface
```
function isSantaClausable(obj) {
 
  if(!(obj instanceof Object) || obj === null){
    return false;
  }
  if('sayHoHoHo' in obj && typeof obj.sayHoHoHo === 'function' && 'distributeGifts' in obj && typeof obj.distributeGifts === 'function' &&'goDownTheChimney' in obj && typeof obj.goDownTheChimney === 'function'){
    return true;
  }else{
    return false;  
  }  
}
```
- [x] 7 kyu https://www.codewars.com/kata/javascript-class-like-objects
```
class Animal{
  constructor(name, type){
    this.name = name;
    this.type = type;
  }
  toString(){
    return `${this.name} is a ${this.type}`;
  }
}
```
- [x] 7 kyu https://www.codewars.com/kata/the-newest-function
```
const newFunction = function f (){
  return f;
}
```
- [x] 7 kyu https://www.codewars.com/kata/fun-with-es6-classes-number-2-animals-and-inheritance
```
class Shark extends Animal {
  constructor(name, age, status) {
    super(name, age, 0, "shark",status);
  }
}

class Cat extends Animal {
  constructor(name, age, status) {
    super(name, age, 4, "cat",status);
  }
  introduce(){
    let str = super.introduce();
    return str + "  Meow meow!"
  }
}

class Dog extends Animal {
  constructor(name, age, status, master) {
    super(name, age, 4, "dog",status);
    this.master = master;
  }
  greetMaster(){
    return `Hello ${this.master}`;
  }
}
```
- [x] 7 kyu https://www.codewars.com/kata/fun-with-es6-classes-number-4-cubes-and-setters
```
class Cube{
  constructor(length){
    this.length = length
  }
  
  get surfaceArea(){
    return (this.length ** 2) * 6
  }
  
  set surfaceArea(area){
    this.length = Math.sqrt(area / 6)
  }
  
  get volume() {
    return this.length ** 3
  }
  
  set volume(vol){
    this.length = Math.cbrt(vol)
  }
}
```
- [x] 6 kyu https://www.codewars.com/kata/fun-with-es6-classes-number-6-fake-files-basic
```
class File {
  #fullName
  #filename
  #extension
  #countString
  #countChar
  #contents
  constructor(fullName, contents) {
    this.#fullName = fullName;
    this.#contents = contents;
    let index = fullName.lastIndexOf('\.');
    this.#filename = fullName.substring(0, index);
    this.#extension = fullName.substring(index + 1);
    this.#countString = 0;
    this.#countChar = 0;
  }
  get fullName() {
    return this.#fullName;
  }
  set fullName(value) {
    return;
  }
  get filename() {
    return this.#filename;
  }
  set filename(value) {
    return;
  }
  get extension() {
    return this.#extension;
  }
  set extension(value) {
    return;
  }
  set contents(value){
    this.#contents = value;
  }
  get contents(){    
    this.#countString = 0;
    this.#countChar = 0;
    return this.#contents;
  }
  getContents() {    
    if(this.#contents.slice(0,1) === "\n"){
      return this.#contents.slice(1);
    }else{
      return this.#contents;
    }    
  }
  write(str) {
    this.#contents += `\n${str}`;
    this.#countChar = 0;
    this.#countString = 0;
  }
  gets() {
    let len = this.#contents.split('\n').length;
    if(this.#countString !== len){
      let str = this.#contents.split('\n')[this.#countString];
      console.log('contents--> ' + this.#contents);
      console.log('gs--> ' + Boolean(str));
      this.#countString++;
      if(!str || str === ' '){
        return this.gets();
      }else{
        return str;
      }      
    }else{
      return undefined;
    }
  }
  getc() {
    let len = this.#contents.length;
    if(this.#countChar !== len){
      let char = this.#contents.slice(this.#countChar, (this.#countChar + 1));
      this.#countChar++;
      return char;
    }else{
      return undefined;
    }
  }
}
```
- [x] 6 kyu https://www.codewars.com/kata/defining-getters-and-setters-on-an-existing-class
```
// class Person {
//   // You can't redeclare "Person", so this won't work...
// }

Object.defineProperty(Person.prototype,'name',{
    get: function(){
      return this.getName();
    },  
    set: function(value){
      let index = value.indexOf(' ');
      this.firstName = value.slice(0, index);
      index = value.lastIndexOf(' ');
      this.lastName = value.slice(index + 1); 
    }
})

//Person.prototype.name = ??? // Will this work?

// Maybe javascript provides the ability to add
// getter and setters to an existing class?
```
- [x] 6 kyu https://www.codewars.com/kata/array-helpers
```
Array.prototype.square = function(){
  console.log(this);
  return this.map(el=>{
    return el**2;
  })  
}
Array.prototype.cube = function(){
  return this.map(el=>{
    return el**3;
  })  
}
Array.prototype.average = function(){
  if(this.length){
    let sum = this.reduce((a,b)=>{
      return a + b;
    })
    return sum/this.length;
  }else{
    return NaN;
  }  
}
Array.prototype.sum = function(){
  return this.reduce((a,b)=>{
    return a + b;
  })  
}
Array.prototype.even = function(){
  return this.filter((el)=>{
    if(el%2 === 0 || el === 0){
      return el;
    }
  })  
}
Array.prototype.odd = function(){
  return this.filter((el)=>{
    if(el%2 !== 0 || el === 0){
      return el;
    }
  })  
}
```
- [x] 6 kyu https://www.codewars.com/kata/array-number-reduce
```
Array.prototype.reduce = function(callback, initVal){
  let arr = [].concat(this);
  let index = 1;
  let prevVal = undefined;
  if(initVal !== undefined){
    prevVal = initVal;
    index = 0;     
  }else{
    prevVal = arr[0];
  }
  while(index < arr.length){
    prevVal = callback(prevVal, arr[index], index, arr);
    index++;
  }
  return prevVal;
}
```
- [x] 6 kyu https://www.codewars.com/kata/extract-nested-object-reference
```
Object.prototype.hash = function getPath(string) {
  let arrPath = string.split('.');
  let obj = this[arrPath[0]];
  if (arrPath.length == 1) {
    return obj;
  } else {
    arrPath.splice(0, 1);
    arrPath = arrPath.join('.');
    return getPath.call(obj, arrPath);
  }
}
```
- [x] 6 kyu https://www.codewars.com/kata/image-host-filename-generator
```
function generateName()
{
  // make sure to check the name is unique via the photoManager object
  //DEC B 65-90 S 97-122
  function randomChar(){
   let charCode = undefined; 
   let ctrl = true;
   while(ctrl){
     charCode = Math.floor(Math.random()*(122 - 65) + 65);
     if(charCode < 91 || charCode > 96){
       ctrl = false;
     }
   }
   return charCode;
  }

  function *gen(callback){
    let set = new Set();
    function exam(generate){
      let code = 0;
      let flag = true;
      while(flag){
        code = generate();
        if(!set.has(code)){
          set.add(code);
          flag = false;
        }
      }
      return code;
    }
    yield exam(callback);
    yield exam(callback);
    yield exam(callback);
    yield exam(callback);
    yield exam(callback);
    yield exam(callback);
    return ;
  }

  let name = [];
 
  let fGen = gen(randomChar);
  for (let value of fGen) {
    name.push(value);
  }
  
  return  String.fromCharCode(...name);
}
```
- [x] 6 kyu https://www.codewars.com/kata/implementing-object-dot-create
```
Object.create = function(prototype, properties) {
  //Your code goes here
  //And remember: you need not to reinvent Object.defineProperties on your own!
  console.log("proto : " + prototype);
  console.log("props : "+properties);
  let exitObject = {};
  if(typeof properties === 'object'){
    Object.defineProperties(exitObject, properties);
  }else{
    Object.defineProperties(exitObject, {});
  }
  if(prototype instanceof Object || prototype === null){
    Object.setPrototypeOf(exitObject, prototype);
  }else{
    throw new TypeError(`Prototype is ${prototype}`, `Wrong code`, 18);
  }  
  return exitObject;
};
```
- [x] 5 kyu https://www.codewars.com/kata/using-closures-to-share-class-state
```
var Cat = (function () {
  var cats = {
    count: 0,
    totalWeight: 0,
    avgWeight: 0
  }
  
  function Cat (name, weight) {
    if (!name || !weight) {
      throw new Error('Both `name` and `weight` should be provided');
    }
    cats.count++;
    this.name = name;

    Object.defineProperty(this, 'weight', {
      get: function () {
        return this._weight || 0;
      },
      set: function (val) {
        cats.totalWeight = cats.totalWeight - this.weight + val;
        cats.avgWeight =  cats.totalWeight / cats.count;
        return this._weight = val;
      }
    });

    this.weight = weight;
  }
  
  Cat.averageWeight = function () {
    return cats.avgWeight;
  }
  
  return Cat;
  
}());
```
- [x] 5 kyu https://www.codewars.com/kata/replicate-new
```
function nouveau (Constructor) {
  // Don't forget, unnamed arguments after Constructor may be passed in!
  console.log(arguments[0].toString());
  let newArguments = [...arguments];
  if(arguments.length > 1){
    newArguments.splice(0,1);
  }else{
    newArguments = [];
  }
  
  let obj = {};

  Object.setPrototypeOf(obj, Constructor.prototype);

  let constructor = Constructor.bind(obj);

  let instance = constructor(...newArguments);
 
  if(!instance){
    return obj;  
  }else{
    console.log(typeof instance);
    if(typeof instance === 'object' || typeof instance === 'function'){
      return instance;
    }else{
      return Object.setPrototypeOf(obj, Constructor.prototype); 
    }        
  }
}
```
- [x] 5 kyu https://www.codewars.com/kata/paginationhelper
```
class PaginationHelper {
  constructor(collection, itemsPerPage) {
    // The constructor takes in an array of items and a integer indicating how many
    // items fit within a single page
    this.collection = collection;
    this.itemsPerPage = itemsPerPage;
  }
  itemCount() {
    // returns the number of items within the entire collection
    return this.collection.length;
  }
  pageCount() {
    // returns the number of pages
    let pages = this.collection.length % this.itemsPerPage;
    if (pages === 0) {
      return this.collection.length / this.itemsPerPage;
    }else{
      let rem = this.collection.length % this.itemsPerPage;
      return ((this.collection.length - rem)/this.itemsPerPage) + 1;
    }
  }
  pageItemCount(pageIndex) {
    // returns the number of items on the current page. page_index is zero based.
    // this method should return -1 for pageIndex values that are out of range
    if(!this.collection.length || pageIndex < 0){
      return -1;
    }
    let pageCount = this.pageCount();
    if((pageIndex + 1) < pageCount){
      return this.itemsPerPage;
    }else if((pageIndex + 1) > pageCount){
      return -1;
    }else{
      if((this.collection.length%this.itemsPerPage) === 0){
        return this.itemsPerPage;
      }else{
        return (this.collection.length - this.itemsPerPage*(pageCount - 1));
      }
    }    
  }
  pageIndex(itemIndex) {
    // determines what page an item is on. Zero based indexes
    // this method should return -1 for itemIndex values that are out of range
    if(!this.collection.length){
      return -1;
    }
    if(itemIndex < 0 || itemIndex > this.collection.length - 1){
      return -1;
    }else if(this.pageCount() === 0){
      return 0;
    }else{
      return (itemIndex - itemIndex%this.itemsPerPage)/this.itemsPerPage;
    }
  }
}
```
- [x] 4 kyu https://www.codewars.com/kata/undo-slash-redo
```
function undoRedo(object) {
  return {
    object: object,
    cache: {
      operationCounter: 0,
      operation: [{
        name: 'start',
        save: Object.assign({}, object)
      }],
      log: function (operationName, obj) {
        this.operationCounter++;
        let copyObject = Object.assign({}, obj);
        let save = {
          name: operationName,
          save: copyObject,
          redo: false
        }
        if (this.operation[this.operationCounter]) {
          this.operation[this.operationCounter] = save;
        } else {
          this.operation.push(save);
        }
      },
      redo: function () {
        if (this.operation[this.operationCounter + 1] && this.operation[this.operationCounter + 1].redo) {
          this.operationCounter++;
          this.operation[this.operationCounter].redo = false;
          return this.operation[this.operationCounter];
        } else {
          throw new Error('Nothing redo');
        }
      },
      undo: function () {
        this.operationCounter--;
        if (this.operationCounter >= 0) {
          if (this.operation[this.operationCounter + 1]) {
            this.operation[this.operationCounter + 1].redo = true;
          }
          return this.operation[this.operationCounter]
        } else {
          this.operationCounter = 0;
          throw new Error('Nothing undo!');
        }
      }
    },
    set: function (key, value) {
      if (this.object.hasOwnProperty(`${key}`)) {
        this.object[`${key}`] = value;
      } else {
        Object.defineProperty(this.object, `${key}`, { value: value, configurable: true, writable: true, enumerable: true});
      }
      this.cache.log('set', this.object);
    },
    get: function (key) {
      if (this.object.hasOwnProperty(`${key}`)) {
        return this.object[`${key}`];
      } else {
        return undefined;
      }
    },
    del: function (key) {
      if (this.object.hasOwnProperty(`${key}`)) {        
        delete this.object[`${key}`];
        this.cache.log('delete', this.object);
      }
    },
    undo: function () {
      let saveObj = this.cache.undo();
      for (const key in this.object) {
        delete this.object[`${key}`]
      }
      Object.assign(this.object, saveObj.save);
    },
    redo: function () {
      let saveObj = this.cache.redo();
      for (const key in this.object) {
        delete this.object[`${key}`]
      }
      Object.assign(this.object, saveObj.save);
    }
  };
}
```