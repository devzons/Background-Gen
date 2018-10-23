# Background-Gen
## let, const
```
const obj = {
  player: 'dev',
  experience: 100,
  wizardLevel: false
}

const player = obj.player;
const experience = obj.experience;
let wizardLevel = obj.wizardLevel;

const { player, experience } = obj;
let { wizardLevel } = obj;
```
---------------------------
const name = "Sally";
const age = 34;
const pet = "horse";

const greeting = `Hello ${name} you seem to be ${age-10}. What a lovely ${pet} you have.`;

---------------------------
function greet( name='', age=40, pet='cat') {
  return `Hello ${name} you seem to be ${age-10}. What a lovely ${pet} you have.`;
}

## Symbol

let sym1 = Symbol();
let sym2 = Symbol('foo');
let sym3 = Symbol('foo');

## arrow function

function add(a,b) {
  return a + b;
}

add = (a, b) => a + b;

------------------

function moveCommand(direction) {
  var whatHappen;
  switch (direction) {
    case "forward":
      whatHappen = "you go forward";
      break;
    case "backward":
      whatHappen = "you go back";
      break;
    case "right":
      whatHappen = "you go right";
      break;
    case "left":
      whatHappen = "you go left";
      break;
    default:
      whatHappen = "please enter a valid direction";
  }
  return whatHappen;
}

----------------------
Closures - 
a function ran. the function executed. It's never going to execute again. But it's going to remember that there are reference to those variables so the child scope always has access to the parent scope.

const first = () => {
  const greet = 'Hi';
  const second = () => {
    alert(greet);
  }
  return second
}

const newFunc = first();
newFunc();

------------------------
Currying
const multiply = (a, b) => a * b;
const curriedMultiply = (a) => (b) => a * b;
curriedMultiply(a)(b);
const multiplyBy5 = curriedMultiply(5);
multiplyBy5(5); // 25
multiplyby5(10); // 50

-----------------------
Compose
const compose = (f, g) => (a) => f(g(a));
const sum = (num) => num + 1;
compose(sum,sum)(5); // 7

### Avoiding Side Effects, functional purity(deterministic)
1. Deterministic --> always produces the same results given the same inputs
2. No Side Effects -->  It does not depend on any state, or data, change during a program’s execution. It must only depend on its input elements.

## Advanced Array

const array = [1,3,10,16];

const double = []
const newArray = array.forEach(num => { 
  double.push(num * 2);
});
console.log('forEach', double);

// map
const mapArray = array.map(num => num * 2);
console.log('map', mapArray);

// filter
const filterArray = array.filter(num => num > 5);
console.log('filter', filterArray);

// reduce ****
const reduceArray = array.reduce((accumulator, num) => {
  return accumulator + num;
}, 0);
console.log('reduce', reduceArray);

ex)
const array = [
  {
    username: "john",
    team: "red",
    score: 5,
    items: ["ball", "book", "pen"]
  },
  {
    username: "becky",
    team: "blue",
    score: 10,
    items: ["tape", "backpack", "pen"]
  },
  {
    username: "susy",
    team: "red",
    score: 55,
    items: ["ball", "eraser", "pen"]
  },
  {
    username: "tyson",
    team: "green",
    score: 1,
    items: ["book", "pen"]
  },

];

let changeArray = [];
array.forEach(user => {
  let {username} = user;
  username = username + "!";
  changeArray.push(username);
});
console.log('forEach', changeArray);

const mapArray = array.map(user =>{
  let {username} = user;
  return username = username + "?";
});
console.log('map', mapArray);

const filterArray = array.filter(user => {
  return user.team === "red";
});
console.log('filter', filterArray);

const reduceArray = array.reduce((accumulator, user) => {
  return accumulator + user.score;
}, 0);
console.log('reduce', reduceArray);

const arrayNum = [1, 2, 4, 5, 8, 9];
const newArray = arrayNum.map((num, i) => {
	return num * 2;
});
console.log(newArray);

const answer = array.map(user => {
	user.items = user.items.map(item => {
		return item + "!"
	});
	return user;
})
console.log(answer);

## Advanced Objects

// reference type
var obj1 = {value: 10};
var obj2 = obj1;
var obj3 = {value: 10 };

// context vs scope
const obj4 = {
  a: function() {
    console.log(this);
  }
}

// instantiation
class Player {
  constructor(name, type){
    console.log('player', this);
    this.name = name;
    this.type = type;
  }
  introduce() {
    console.log(`Hi Iam ${this.name}. I'm a ${this.type}`);
  }
}

class Wizard extends Player {
  constructor(name, type){    
    super(name, type);
    console.log('wizard', this);
  }
  play() {
    console.log(`WEEE I'm a ${this.type}`);
  }
}

const wiz1 = new Wizard('Sean', 'Healer');
const wiz2 = new Wizard('Shaw', 'Dark Magic');

ex)
//#3 create two classes: an Animal class and a Mamal class. 
// create a cow that accepts a name, type and color and has a sound method that moo's her name, type and color. 
class Animal {
	constructor(name, type, color) {
		this.name = name;
		this.color = color;
		this.type = type;
	}
}

class Mamal extends Animal {
	constructor(name, type, color) {
		super(name, type, color);
	}
	sound() {
		console.log(`Moooo I'm ${this.name} and I'm a ${this.color} ${this.type}`);
	}
}

const cow = new Mamal('Shelly', 'cow', 'brown');

## ES7

.includes()

a**2
a**3

## ES8

padStart(), padEnd()

'Turtle'.padStart(10); // "    Turtle"
--------------------------------------
Object.values
Object.entries
Object.keys
--------------------------------------
ex
let obj = {
  username0: 'John',
  username1: 'Jane',
  username2: 'Joe'
}

Object.keys(obj).forEach((key,index)=>{
  console.log(key, obj[key]);
});
username0 John
username1 Jane
username2 Joe

Object.values(obj).forEach(value=>{
  console.log(value);
});
John
Jane
Joe

Object.entries(obj).forEach(value=>{
  console.log(value);
});
["username0", "John"]
["username1", "Jane"]
["username2", "Joe"]

Object.entries(obj).map(value=>{
  return value[1] + value[0].replace('username', '');
});
["John0", "Jane1", "Joe2"]

let obj2 = {
  my: 'name',
  is: 'Rudolf',
  the: 'raindeer'
}
Object.entries(obj2).map(value=> value.join(" ")).join(' ');

const startLine = '     ||<- Start line';
let turtle = '🐢';
let rabbit = '🐇';
// when you do:
console.log(startLine.padStart(20));
console.log(turtle.padStart(10));
console.log(rabbit.padStart(10));

## Debugging

const flattened = [[0, 1],[2, 3],[4, 5]].reduce(
  (a,b) => a.concat(b), []);

==>
const flattened = [[0, 1],[2, 3],[4, 5]].reduce((accumulator, array) => {
  return accumulator.concat(array);
}, []);

const flattened = [[0, 1],[2, 3],[4, 5]].reduce((accumulator, array) => {
  console.log('accumulator', accumulator);
  console.log('array', array);
  return accumulator.concat(array);
}, []);

const flattened = [[0, 1],[2, 3],[4, 5]].reduce((accumulator, array) => {
  debugger;
  return accumulator.concat(array);
}, []);

## javascript Run-Time Environment

// CALL STACK

// WEB API

// CALLBACK QUEUE

// EVENT LOOP

console.log('1');
setTimeout(()=>{ console.log('2');},0);
console.log('3');
1
3
2

element.addEventListener('click', () => {
  console.log('click');
});

## Modules

-----CommonJS + Browserify --------------
module.exports = function add(a, b) {
  return a * b;
}

var add = require("./add");

---- ES6 + Webpack2 ----------------------
// js1
export const add = (a, b) => a + b;
// or
export default function add() {
  return a + b;
}

// js2
import { add } from './add';
// or
import add from './add';
