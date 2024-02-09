---
type: NoteCard
tags: []
---

# lab - Web Transpilers
Web transpilers are systems for source-to-source transformations, also called compilers or transcompilers.

There are many non-native javascript programming languages. This includes the most famous ones: ECMAScript and Typescript, but there are others like CoffeeScript, Elm, Dart, ClojureScript, PureScript, and many more. Non-javascript languages need to be compiled into javascript.

ECMAScript is a superset language for JavaScript (and JScript by Microsoft). ECMAScript maintains the standard and future features of JavaScript. We can think of it as modern JavaScript syntax. Simply put, ECMAScript has many modern features that are not yet implemented by JavaScript current clients (browsers). However, browsers’ support of modern JavaScript features is relatively slow. In other words, many modern features of ECMAScript Transpilers enable developers to use the latest features of non-javascript languages because they compile the source code into versions of JS that current browsers support.

Popular Transpilers:

*   Babel: For modern JavaScript syntax (ECMAScript)
*   Typescript: For typescript language
*   Esbuild: Support both typescript and modern JavaScript

## Lab - Esbuild

Let us continu on the previous :ref[lab - Web Bundler]{path='/notes'} using esbuild (<https://esbuild.github.io/>). Esbuild is a web bundler but also a transpiler. It can transpile ECMAScript and Typescript into JavaScript.

Esbuild will transpile the `entryPoints` into a `target` version of javaScript, which is `es2020` in the example below.

```js
export async function buildApp() {
  const prod = process.argv[2] === 'production';
  const entry = process.argv[3];

  // check the different options https://esbuild.github.io/api
  const context = await esbuild.context({
    banner: {
      js: banner,
    },
    entryPoints: [`src/${entry}`],
    bundle: true,
    // splitting: true,
    external: [...builtins],
    logLevel: 'error',
    sourcemap: prod ? false : 'inline',
    treeShaking: true,
    outfile: './build/app.js',
    minify: prod,
    plugins: [],
    loader,
    format: 'cjs',
    target: 'es2020',
  });
```