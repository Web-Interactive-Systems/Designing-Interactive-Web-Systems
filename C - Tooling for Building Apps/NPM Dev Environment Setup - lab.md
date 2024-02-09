---
type: NoteCard
tags: []
---

# NPM Dev Environment Setup - lab
## Installation

Here are the steps to set up a dev environment for web programming using JavaScript, VS Code, and Chrome.

*   Install Node.js: Go to the Node.js website ([https://nodejs.org/](https://nodejs.org/fr/)) and download your operating system's latest version of Node.js. Follow the installation instructions.
*   Install VS Code: Go to the VS Code website (<https://code.visualstudio.com/>) and download your operating system's latest version of VS Code. Follow the installation instructions.
*   Install Chrome: Go to the Google Chrome website and download your operating system's latest version of Chrome. Follow the installation instructions.

## First NPM Project

Latter, we will see frameworks, such as vite that speeds up the development process

*   Create a project folder, for example, **WebCourse**. Open a terminal or command prompt and navigate to the folder.

*   Create a folder **lab1** inside **WebCourse**. Then navigate to the folder using your terminal.

*   Initialize **lab1 as** a Node.js project:

    *   In the terminal or command prompt
    *   run the command **`npm init`**
    *   Follow the prompts to create a new Node.js project
    *   This will create a **`package.json`** file in your project folder
    *   Explore **`package.json`**

*   Install a web server:

    *   In the terminal or command prompt
    *   run the command **`npm install -g http-server`**
    *   This will install the **`http-server`** package globally because we use **`-g`**` argument`

*   Create an HTML file:

    *   Create a new file in your **lab1** folder called **`index.html`**
    *   Add some basic HTML code to the file

*   Start the web server:

    *   In the terminal or command prompt
    *   run the command **`http-server`**
    *   This will start the web server and serve your **`index.html`** file
    *   Identify the **port** that **http-server** uses

*   Open Chrome:

    *   Open Chrome and navigate to [**`http://localhost:808`**](http://localhost:8080/)**`1`** (if **8081 is the port**)
    *   You should see your **`index.html`** file

*   Modify your file **`index.html`**