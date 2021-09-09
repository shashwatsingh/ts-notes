# Some terms when dealing with types

## We already think in types

Writing code requires thinking about the kind of value we're working with:

- I want to get max number from this array: array of numbers
- I want to find an object with `ID = 100` (we're assuming there are objects with this key): array of objects, each having an ID property which is a number
- I'll call this function with ID parameter value 100 and it'll return me a matching object with that ID (or null if missing)
- This component requires boolean props `<Action isDisabled=true></Action>`

This expectation isn't written in JS.

You want to convey the pre-conditions (aka what the calling code should do so that your code works as expected) to the callers.

TS allows you to write this in your code, which editors understand. 

So less bugs, less debugging.


## Two worlds: types & code

Imagine there's a set of glasses (like in Mr India or IronMan, but not as exciting).

For example, when you write this (the JS world):

```js
let x = true; // a JS expression
```

You see this with the glasses on (the type world):

```cs

let   // will change value later as didn't use `const`
x     // name of the variable `x`
=     
true; // of type boolean (since true is an element of boolean)
      // since the value is of type boolean, the variable's type is also boolean

// ->

let x: boolean = true;

```

You have a way to "peek" into how your program will be understood
by the JS environment during runtime, without even running it.

## Relation between Values and Types

Consider the following:

```ts
let x = 10;   // a variable is holding a value "10"
let y = "hi"; // a variable is holding a value "hi"

console.log(typeof(x)); // number

console.log(typeof(y)); // string

```

So the first distinction is that values and types are different. A value can be of a certain type. 

A value is a "single thing" and *set of* one or more values together, is a type.


## Primitive types as Sets

Think about `true` as a value. You cannot modify it, nor delete or 
add a different value with the same "data" -- it can distinctly only 
be `true`. 

It is a distinct value that I can use in my programs but I cannot
change it in any way -- it is "available" as programs are
running in browser/node (which is a platform).

`false` is another such value.

`true` and `false` together, are what we mean when we say `boolean`.

In other words, boolean set consists of two values: true and false.
Technically, nothing stops me from using only `true` in my programs. 

TypeScript, the language, allows us to convey this in source-code 
which *may* be enforced by TypeScript, the compiler.






