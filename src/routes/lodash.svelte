<div class="main-div">
<h1 class="head-lines">Why Lodash?</h1>
<p class="info">
    Lodash makes JavaScript easier by taking the hassle out of working with
    arrays, numbers, objects, strings, etc. Lodash’s modular methods are great
    for: > Iterating arrays, objects, & strings > Manipulating & testing values
    >Creating composite functions
</p>
<h1 class="head-lines">What You Already Can Do Without Lodash</h1>
<p class="info">
    This is a partial list of Lodash tasks that can now be replaced with vanilla
    JavaScript. If you use Lodash just for these utilities, you can replace with
    Vanilla and remove the dependency. Concatenate arrays, without mutating the
    original array:
</p>
<code>
    let oneStooge = ["Moe"]; let twoStooges = ["Larry", "Curly"]; // Both create
    ["Moe", "Larry", "Curly"] let threeStoogesLodash = _.concat(oneStooge,
    twoStooges); let threeStoogesVanilla = [...oneStooge, ...twoStooges];
</code>
<p class="info">Fill part of an array with a single value (mutates the array):</p>
<code>
    let someArray = [100, 99, 98, 97, 96, 95]; let someArrayCopy =
    [...someArray]; _.fill(someArray, 0, 2, 5); // [100, 99, 0, 0, 0, 95]
    someArrayCopy.fill(0, 2, 5); // [100, 99, 0, 0, 0, 95]
</code>
<h1 class="head-lines">But Sometimes You Do Need Lodash</h1>
<p class="info">Not every Lodash utility is available in Vanilla JavaScript. You can't deep clone an object, for example. That's why these libraries are far from obsolete. But if you're loading the entire library just to use a couple of methods, that's not the best way to use the library.

You can import just the functions you need. For example:</p>
<code>
   // In ES6 module style:
import map from "lodash/map";
import cloneDeep from "lodash/cloneDeep";

// Or their CommonJS counterparts:
const map = require("lodash/map");
const cloneDeep = require("lodash/cloneDeep"); 
</code>

<h2 class="head-lines">other examples of code from "lodash"</h2>
<p class="info">With Lodash, there’s a unified _.forEach, for both array and object:</p>
<code>
    _.forEach(obj, (value, key) => { console.log(value) })
</code>
<h2 class="head-lines">Chain and Lazy Evaluation</h2>
<code>
    
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
let lines = `
an apple orange the grape
banana an apple melon
an orange banana apple
`.split('\n')

_.chain(lines)
  .flatMap(line => line.split(/\s+/))
  .filter(word => word.length > 3)
  .groupBy(_.identity)
  .mapValues(_.size)
  .forEach((count, word) => { console.log(word, count) })

// apple 3
// orange 2
// grape 1
// banana 2
// melon 1
</code>
<h2 class="head-lines">Destructuring, Spread and Arrow Function</h2>
<code>
    // Lodash
_.head([1, 2, 3]) // => 1
_.tail([1, 2, 3]) // => [2, 3]
// ES6 destructuring syntax
const [head, ...tail] = [1, 2, 3]

// Lodash
let say = _.rest((who, fruits) => who + ' likes ' + fruits.join(','))
say('Jerry', 'apple', 'grape')
// ES6 spread syntax
say = (who, ...fruits) => who + ' likes ' + fruits.join(',')
say('Mary', 'banana', 'orange')

// Lodash
_.constant(1)() // => 1
_.identity(2) // => 2
// ES6
(x => (() => x))(1)() // => 1
(x => x)(2) // => 2

// Partial application
let add = (a, b) => a + b
// Lodash
let add1 = _.partial(add, 1)
// ES6
add1 = b => add(1, b)

// Curry
// Lodash
let curriedAdd = _.curry(add)
let add1 = curriedAdd(1)
// ES6
curriedAdd = a => b => a + b
add1 = curriedAdd(1)
</code>
</div>

<style>
  
    .main-div {
        text-align: center;
        background-color: greenyellow;
    }
    .info {
        text-align: center;
    }
    .head-lines {
        color: red;
        text-align: center;
    }
    .our-anchors {
        text-align: center;
        list-style-position: inside;
    }
</style>

