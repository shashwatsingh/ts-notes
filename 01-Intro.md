
# TypeScript Notes


## Why?

As applications grow (maybe to hundreds of screens with large stores), 
mismatch in different areas of code (functions defined in moduleA,
used in a MyComponentB, reading a redux store in a moduleD) simpler 
issues like if a callback function gets an index or an object as first 
parameter becomes an issue.

TypeScript helps you do:

- *Optional* type-checking in source-code

  - predictable refactoring: find all usages of a variable, function, class;rename or delete unused code; control-flow analysis (unreachable code, unhandled conditions).

  - catch errors early: when writing code instead of when running it

- Pollyfills for unimplemented (but planned) language features

- Convey intent of code more clearly

- Documentation: types are the best form of documentation; never gets out-of-date

## What

Depending on context, TypeScript could refer to:

- compiler (.TS -> .JS)
- language
- tooling around it (language server, editor integrations, analyzers) 

Latest details found on: [official docs](https://www.typescriptlang.org/docs). 

## How? 

- Local: `npm install -g typescript` + VSCode

- Online: [TS Playground](https://www.typescriptlang.org/play) to try various features and see the output JS, and even the AST.

