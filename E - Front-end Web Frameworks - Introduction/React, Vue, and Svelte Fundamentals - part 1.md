---
type: NoteCard
tags: []
---

# React, Vue, and Svelte Fundamentals - part 1
## Creating an app

Like any modern web framework, the recommended way to scaffold an app is to use a toolchain, such as webpack, esbuild, vite, parcel, or others. Vite (created by the creator of vuejs) is recommended.

### **Apps templates**

The Vite community has created various templates to scaffold web apps using different technologies, such as vanilla javascript, typescript, web workers, and others.

Always check the documentation because it might change: <https://vitejs.dev/>.

For react

    yarn create vite react-app --template react

For Vue

    yarn create vite vue-app --template vue

For Svelte

    yarn create vite svelte-app --template svelte

### **Apps structure**

Explore the structure of the folders: react-app, vue-app, and svelte-app.

Important common files are:

*   `package.json`: It contains the list of dependencies for your app, as well as some metadata and `eslint` configuration
*   `jsconfig.json`: It contains a config for IDEs (like VS Code and other text editors). It supports project structure and assists in auto-completion
*   `vite.config.js`: It contains config for the Vite build (see <https://vitejs.dev/config/> for more information)
*   `src`: It contains the code source of the app and can be structured in different ways depending on the size of the app
*   `assets`: It contains static files used in the app, such as images, videos, audios, etc. This assets will be processed for optimization by the Vite build system.
*   `public`: It contains static assets used in the app, such as images but they are not processed by the build (e.g., hashing), i.e., they will be served as-is to the clients (browser).