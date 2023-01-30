- [x] 7 kyu https://www.codewars.com/kata/singleton-pattern
```
var Singleton = function(){
    // implement singleton Class
      if (Singleton.instance) {
        return Singleton.instance;
      }
      Singleton.instance = this;
      return Singleton.instance;
};
```
- [x] 7 kyu https://www.codewars.com/kata/patterncraft-adapter
```
class MarioAdapter{
  constructor(hero) {
    this.hero = hero;
  }

  attack(target) {
    console.log(target.health);
    const dmg = this.hero.jumpAttack();
    target.health -= dmg;
  }
}
```
- [x] 7 kyu https://www.codewars.com/kata/patterncraft-visitor
```
class Marine {
  constructor() {
    this.health = 100;
  }
  accept(visitor) { 
    this.health = visitor.visitLight(this.health);
  }
}

class Marauder {
  constructor() {
    this.health = 125;
  }
  accept(visitor) { 
    this.health = visitor.visitArmored(this.health);
  }
}

class TankBullet {
  visitLight(unit) {
    return unit - 21;
  }
  visitArmored(unit) {
    return unit - 32;
  }
}
```
- [x] 6 kyu https://www.codewars.com/kata/patterncraft-state
```
class SiegeState {
  constructor() {
    return {state: false};  
  }
}

class TankState {
  constructor() {
    return {state: true};  
  }
}

class Tank {
  constructor() {
    this.state = {state: true};  
  }

  get canMove() {
    return this.state.state;
  }
  get damage() {
    if (this.state.state) return 5;
    return 20;
  }
}
```
- [x] 6 kyu https://www.codewars.com/kata/patterncraft-strategy
```
class Fly {
  move(unit) { return unit + 10; }
}

class Walk {
  move(unit) { return unit + 1; }
}

class Viking {
  constructor() {
    this.position = 0;
    this.moveBehavior = new Walk();
  }
  
  move() { this.position = this.moveBehavior.move(this.position); }
}
```
- [x] 6 kyu https://www.codewars.com/kata/patterncraft-decorator
```
class Marine {
  constructor(_damage, _armor) {
    this.damage = _damage;
    this.armor = _armor;
  }
  
  get damage() { return this._damage }
  set damage(value) { 
    this._damage = value;
  }
  
  get armor() { return this._armor; }
  set armor(value) { 
    this._armor = value;
  }
}

class MarineWeaponUpgrade {
  constructor(marine) {
    this.damage = marine.damage;
    this.armor = marine.armor;
  }
  
  get damage() { return this._damage }
  set damage(value) { 
    this._damage = value + 1;
  }
  
  get armor() { return this._armor; }
  set armor(value) { 
    this._armor = value;
  }
}

class MarineArmorUpgrade {
  constructor(marine) {
    this.damage = marine.damage;
    this.armor = marine.armor;
  }
  
  get damage() { return this._damage }
  set damage(value) { 
    this._damage = value;
  }
  
  get armor() { return this._armor; }
  set armor(value) { 
    this._armor = value + 1;
  }
}
```
- [x] 6 kyu https://www.codewars.com/kata/create-iterator
```
const createIterator = (array) => {
  let obj = {
    _array: array,
    index: 0,
    _length: array.length,
    next: function() {
      if (this.index === this._length) {
        return {
          value: undefined,
          done: true
        }
      }
      let value = this._array[this.index];
      this.index++;
      return {
        value: value,
        done: false
      };
    }
  };
  return obj;
};
```
- [x] 6 kyu https://www.codewars.com/kata/sortable-shapes
```
class Shape {
  setArea(area) {
    this.area = area;
  }
  valueOf() {
    return this.area;
  }
}

class Square extends Shape {
  constructor(side) {
    super();
    this.calcArea(side);
  }
  
  calcArea(side){
    this.setArea(side ** 2);
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.calcArea(width, height);
  }
  
  calcArea(width, height){
    this.setArea(width * height);
  }
}

class Triangle extends Shape {
  constructor(base, height) {
    super();
    this.calcArea(base, height);
  }
  
  calcArea(base, height){
    this.setArea((base * height) / 2);
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.calcArea(radius);
  }
  
  calcArea(radius){
    this.setArea((radius ** 2) * Math.PI);
  }
}

class CustomShape extends Shape {
  constructor(area) {
    super();
    this.setArea(area);
  }
}
```
- [x] 4 kyu https://www.codewars.com/kata/dependency-injection
```
var DI = function (dependency) {
  this.dependency = dependency;
};

// Should return new function with resolved dependencies
DI.prototype.inject = function (func) {
  // Your code goes here
  let fStr = func.toString();
  console.log(fStr);
  let index = fStr.indexOf('(');
  fStr = fStr.slice(index + 1);
  index = fStr.indexOf(')');
  fStr = fStr.slice(0, index);
  let arr = fStr.split(', ');
  let fArr = arr.map(f => this.dependency[f]);
  return function() {
    if (fArr.length && !fArr[0]) {
      return func.call(this);
    }
    return func.apply(func, fArr);
  };
}
```