# Sources of gathering types

There are various sources from which TS gathers type information.

First, there's language builtins

## Primitives

1. There are primitive types:

   - string, number, boolean: "hi", 100, true
   - bigint, symbol: BigInt(100), Symbol("my-local-storage-key")
   - object: { id: 100, name: 'Ram' }
   - function: (x) => x * x

Each of these are built into the runtime (node or browser).

2. Then there are collections: `any[]` or `number[]` or 
(we'll get into generics later) `Array<T>`.

3. Special types: 
   - `null` (value is missing)
   - `undefined` (value is unknown)
   - `never` & `unknown`: an impossible type & an unknown type
   - `any` which should be avoided since it effectly satisfies anything, effectively turning off benefits of TS


## Implicit

```ts
let x = 100;
x = true; // this will be flagged: boolean assigned to number
```

This is also described as: typescript is inferring types 
from existing code.

## Explicit

You don't leave typescript to determine the type. Instead, you specify it:

```ts
let x: number = 100;
```

## Structural

Just like one or more primitive values together can be labeled as a type,
the structure of an object: 

```ts
// 1. Define a type

// one number field called 'id',
// another string field called 'name', and 
// another number field 'age' 
// translating the above into typescript:
let p: { id: number, name: string, age: number} = {
    id: 100,
    name: "Ram",
    age: 16,
}

// that was too verbose.
// give it a *type alias* Person
type Person = {
    id: number,
    name: string,
    age: number
};

// 2. Use it in a variable
let p: Person = {
    id: 10, 
    name: 'Ram',
    age: 16,
};

// 3. Use it as a parameter
function getAge (p: Person) { return p.age; }

// 4. Use it as a return type
function copy(p: Person): Person {
    return {
        ...p
    };
}

```

Since types in the context of objects is just a shorthand of describing
the "shape" of your object, their equality is also structually equivalent:

```ts
let p1: { id: number, name: string, age: number} = {
    id: 10, 
    name: 'Ram',
    age: 16,
};

// before, when labeling with `type` keyword
// a more preferred way is to use `interface`
// that was too verbose.
// give it a label = Person
interface Person {
    id: number,
    name: string,
    age: number
};

// since both p1 and p2 are "structurally" same
// meaning all their property-names and types are same
// the type is considered "compatible":
let p2: Person = p1; // this works
```

Learn more here: https://www.typescriptlang.org/play?q=29#example/structural-typing

## Control-flow analysis

TypeScript also understands if-else or switch statements that confirm types:

```ts
function printAll(strs: unknown) {
    if (typeof strs === "string") {
        console.log(strs); // TS knows here strs is a string
    } else if (typeof strs === "boolean") {
        console.log(strs); // or an object
    } else if (typeof strs === "object") {
        // it also understands there's a possibility
        // that strs could be null (which is also an object)
        //
        // `console.log(typeof(null)) // => "object"`
        for (const s of strs) {
            console.log(s);
        }
    } else {
        // do nothing
    }
}
```

See more here: https://www.typescriptlang.org/play?q=185#example/type-guards

## Ambient types

Kind of important for libraries, but good to know of its existence: 
these come from type-definitions, which are extra files that TS 
loads depending on configuration.

Say you're using a third party library like jQuery:

```ts
$('p').hide(); // here TS doesn't know about this type

// but you can let him know about it:

declare var $: any;

// or even load it from the internet 
// see https://github.com/DefinitelyTyped/DefinitelyTyped

```

Ambient types basically say: I'm using a type that's 
provided to you by someone else (possibly outside of your program).