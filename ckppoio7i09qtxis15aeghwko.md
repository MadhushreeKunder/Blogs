## const, let, var when to use what?

 
Up until now, you must have been using `var` to declare a variable in Javascript. But with ES6 came two new ways of declaring variables: `let` and `const`. But why ditch `var` in the first place?🤔


![Thinking](https://media.giphy.com/media/lKXEBR8m1jWso/giphy.gif)

Let us understand using the following piece of code:
 
If you run `getAge(false)`  what output do you expect?
 
```
function getAge(isYoung) {
  if (isYoung) {
	var young = "Kiddo is full of energy!";
  } else {
	var old = "Elderly are very experienced!";
	console.log(young);
  }
} 
```
 
#### Options:
1. Elderly are very experienced!
2. Kiddo is full of energy!
3. ReferenceError: young is not defined
4. undefined
 
![DrumRoll](https://media.giphy.com/media/116seTvbXx07F6/giphy.gif)

If you thought `undefined`, then you are absolutely correct! 🎉
But why `undefined`?

### Hoisting
So in your browser before executing any JS code, all the variables declared with `var` are raised to the top of the function scope, in other words, ** [hoisted](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) **. So at run-time the function   `getAge(false)` looks like this:
 
```
function getAge(isYoung) {
  var young, old;
  if (isYoung) {
	young = "Kiddo is full of energy!";
  } else {
	old = "Elderly are very experienced";
	console.log(young);
  }
}
```
 
### let and const
 
When using `var`, variables are either scoped globally or locally to the function scope. So, how do we eliminate **hoisting**? The solution would be something that scopes the variable to the block (block-scoping); `let` and `const` do exactly this. Variables declared with `let` and `const` inside a code block can only be accessed after they have been declared. The variables are stuck in the ** [Temporal Dead Zone](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#temporal_dead_zone_tdz) ** until the declaration is processed.
 
Now that the variables are declared with `const`, what do you expect to be the output from running `getAge(false)`?
```
function getAge(isYoung) {
  if (isYoung) {
   const young = "Kiddo is full of energy!";
  } else {
   const old = "Elderly are very experienced";
	console.log(young);
  }
}```
 
1. Elderly are very experienced!
2. Kiddo is full of energy!
3. ReferenceError: young is not defined
4. undefined
 
A `ReferenceError` will be thrown because `young` is not declared inside the `else` statement, the `function scope`, or the `global scope`; which is exactly what we wanted. The variable is not being accessed outside its block.

### Rules for using `let` and `const`
`let` and `const` also have some other interesting properties.
1. Variables declared with `let` can be reassigned but can’t be redeclared in the same scope.
2. Variables declared with `const` must be assigned an initial value, but can’t be redeclared in the same scope, and can’t be reassigned.
 
Guess the output for the following code!
```
let color = "Orange";
    color = "Blue";
console.log(color);
```
1. Undefined
2. Orange
3. Blue
4. SyntaxError: Identifier 'color' has already been declared
 
If you said **Blue** then you are absolutely correct!🎉 Because `let` lets the variable be reassigned.

![Pun](https://media.giphy.com/media/3oEduG8nljrAsExGg0/giphy.gif)
 
What do you expect to be the value of `color` from running the following code?
```
const color = "Orange";
color = "Blue";
 ```
1. Orange
2. Blue
3. TypeError: Assignment to constant variable.
4. SyntaxError: Identifier 'color' has already been declared
 
The answer is 3. It gives `TypeError`. Because as we learnt above, variables declared with `const` cannot be reassigned.
 
What will happen when you run `obj`? Will `a` get a new value of 22 or will it be 1?
```
const obj = { a:1, b:2 }
obj.a = 22;
 ```

The answer is `obj` will return `{ a:22, b:2 }`
 
Now consider,
```
const obj1 = { a:23, b:33 }
obj = obj1;
```
What is the answer here? Will the contents of `obj1` be assigned to `obj?`

![Nope](https://media.giphy.com/media/wYyTHMm50f4Dm/giphy.gif)
Nope. 
It gives, `TypeError: Assignment to constant variable.`
 
This is because the `const` declaration creates a read-only reference to a value. It does not mean the value it holds is immutable—just that the variable identifier cannot be reassigned. In our case where the content is an object, the object's contents, what is inside the object can be altered, just that the reference cannot be changed.
 
 
### Summary
Now we have learnt that we can use `let` when we want to reassign new values to a variable. But if new values won't be reassigned to a variable, then it's good practice to declare it with `const`. 
Now that is sorted, what is left is `var`. You shouldn't really use `var` unless you want to declare a variable globally, which is often considered bad practice.
So, now you can start using `let` and `const` in your codebase and save yourself from making mistakes! Happy Coding!

![Yay](https://media.giphy.com/media/31lPv5L3aIvTi/giphy.gif)
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 

