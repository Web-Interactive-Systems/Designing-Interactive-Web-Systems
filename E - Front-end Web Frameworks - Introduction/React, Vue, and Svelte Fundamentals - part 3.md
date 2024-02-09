---
type: NoteCard
tags: []
---

# React, Vue, and Svelte Fundamentals - part 3
## Building an app for production

The command \`yarn dev\` starts dev server on your local machine. However, when the app is ready for deployment, we need to bundle the app for production. The command \`yarn build\` generates an optimized build for deployment. It generates a folder with all the files and assets of the app. This folder is often by default called `dist `(for distribution). The name of the build folder can be changed in the `vite.config.js`.

Build your app using the following command:

    yarn build

When the build is finished, it is always good to check if the production build of the app works as expected. Vite provides \`"preview": "vite preview"\` command to do so. It will start a local static web server that serves the files from `dist` folder using a localhost URL.