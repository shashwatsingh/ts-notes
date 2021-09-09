# Getting Started

## Setting up environment

You need the following to start:

- Node
- Git (good-to-have)
- TypeScript compiler/tooling: `npm install --global typescript`
- Editor compatible with the TypeScript tooling: VSCode

## Setting up the project

TypeScript is a compiler (and related tooling) that takes 
.ts file and outputs .js file.

We can "talk" with this compiler using a config file: tsconfig.json.

So we'll create a new project with an initial configuration:

```bash
mkdir todo

cd todo

npm init --yes

mkdir src
```

Then create a new file:

```bash
code tsconfig.json
```

And paste the following contents in it and save. 

Full details of what this file allows is [documented here](https://www.typescriptlang.org/tsconfig)

```json
{
    "compilerOptions": {
        "target": "es2018",
        "outDir": "./dist",
        "rootDir": "./src",
        "module": "commonjs"
    }
}
```

This completes our setup and we can start writing some TS.

## Compile and run


Create a new file `src\todo.ts`:

```ts
const name = 'Ram';
console.log(name);
```

Then ensure that you're still inside the `todo` folder, and run `tsc`. 

This will create a new file `dist\todo.js`. You can run this file:

```
node dist\todo.js
```

and you should see the output.

## Exercise

Change it as follows:

```ts
const name = 'Ram';

name = 'Shyam';

console.log(name);
```

Can you understand what the editor says? 
What happens when you run `tsc` again?
How do can fix it and run it again?
