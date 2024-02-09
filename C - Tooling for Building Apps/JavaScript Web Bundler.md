---
type: NoteCard
tags: []
---

# JavaScript Web Bundler
Web bundlers are systems that processes multiple source files and bundles them into a single or a few optimized files ready to be served by a web server.

Modern web apps rely on a lot of source files, such as HTML, JS, CSS, images, and other types of files. Managing multiple files in an application can be challenging. Bundlers enable developers to organize and manage all their files in one place.

A typical web bundler provides ways to:

*   Code optimization: Enhancing code bundle (e.g., compression, minification)
*   Files bundling: Processing and packing source files into an optimized files (outpu)
*   Code compartmentalization: Enabling a modular organization of the code base
*   Hot module replacement or reload (HMR): Apply code changes in real-time to pages, removing the need to refresh the page with each change
*   Code tree-shaking: Detecting and removing unused code and imports, thus reducing bundle size
*   Code source-map: Enable debugging the bundle code even if already optimized (e.g., minified)
*   Code visualizer: Help analyze the code base (e.g., dependencies, etc.)

## Lab - Esbuild

One of the raising web bundler is esbuild (<https://esbuild.github.io/>). To understand the main concept of a web bundler, we provide steps below to bundle the portfollio app (that we created in the a previous lab) using esbuild instead of parcel. You must follow the documentation of esbuild and complete the below steps:

*   Install esbuild
*   Create a script to run your portfollio app using esbuild dev server
*   Create a build script to build your portfollio app using esbuild
*   Add CSS minification in the build script
*   Add source map in the build script

Here is an example with some comments.

```js
import * as esbuild from 'esbuild';
import process from 'process';
import builtins from 'builtin-modules';


const banner = `/*
Copyright...
*/
`;

const loader = {
  '.png': 'dataurl',
  '.svg': 'dataurl',
  '.jpeg': 'dataurl',
  '.jpg': 'dataurl',
  '.woff': 'dataurl',
  '.woff2': 'dataurl',
  '.eot': 'dataurl',
  '.ttf': 'dataurl',
  '.ttf': 'dataurl',
};

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

  // Manually do an incremental build
  await context.rebuild();

  // Enable watch mode
  await context.watch();

  // Dispose of the context
  context.dispose();
}

// run the build
buildApp();
```