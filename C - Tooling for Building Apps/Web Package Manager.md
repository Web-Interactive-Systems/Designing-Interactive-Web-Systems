---
type: NoteCard
tags: []
---

# Web Package Manager
Packages managers are important part of modern web design development. A simple definition of a package is:

> A system that manages dependencies and other tasks for a project.

Modern web projects rely on a lot of dependencies to manage and speed up different parts of the developments. For example, a project might need to manipulate and display dates in human-readable formats, which can be challenging to do properly. Chances are that someone else worked hard and has solved this problem. It might prove useful to use existing libraries for specific problems and needs rather than trying to write the code to solve such problems.

A typical package manager provides a way to:

*   Install and remove dependencies
*   Find dependencies of a project
*   Audit dependencies for vulnerabilities
*   Automate tasks, commands, and scripts for a project, such as build, lint, serve, etc.

## Known Managers

Here a list of famuous package managers

*   npm
*   yarn
*   parcel
*   pnpm

Each package manager has its strenghts and weakness. NPM is the precursor of the all the existing managers. It refers to Node Package Manager (NPM). Actually, we can use these packages to manager frontend and backend projects that use javascript or nodejs. Nodejs is a javascript framework to create servers. A nodejs server is basically javascript code that runs on the server, which could be an http server, a socket server, an application server, etc. We will explore nodejs in the second module of this course.

## Using a package manager

Packages managers work using a \`command line\`. A command line is type of application when we write commands to perform actions or tasks. A command line follows the following pattern: `THE_PROGRAM THE_COMMAND [ARGUMENTS]`. Soem commands may have arguments other may not.

Package managers offer similar APIs of how they work. Here is some of the main commands:

*   Create an npm project, inside a folder, e.g., `my-npm-app`

    *   `yarn init `(using yarn)
    *   `npm init `(using npm)

*   Install a dependency

    *   `yarn add`
    *   `npm install`

*   Remove a dependency

    *   `yarn remove`
    *   `npm uninstall`

The `yarn init `or `npm init` will create an important file called `package.json`. This file is the manifest of the project. It contains information, such as dependencies, scripts, and others.

Dependencies that we install, for example, \`yarn install\`, are added to the `package.json` file and downloaded and saved inside the folder `node_modules`.

## Package.json file

The file `package.json` is the file where the package manager stores dependencies for a project. Often dependencies are separated into ***dependencies*** and ***devDependencies***. Dependencies are the libraries that an app uses at runtime. These will be bundled and packaged with the app in production mode. DevDependencies are libraries used only for development. They are not added to the bundle in production mode.

Package.json stores other meta-data for a project, such as project name, version, etc.

## Lock file

Package managers have a file called lock file. For yarn is called yarn.lock and for npm is called package.lock. The lock file is always generated and should never be changed manually. It contains the fixed versions that the project depends on.

A project may depend on different dependencies with different versions. Dependencies of a project also their own dependencies. In addition, dependencies depend on each other. Package managers will parse all the dependencies in a project including their sub-dependencies and resolve the dependency tree for a project. The resolved dependency tree is written in the lock file.

::::cal
It is good practice to look for dependencies with less to zero dependencies. By doing so:

*   you minimize the bundle size
*   you lower the risque of conflict between dependencies
*   you lower the risque of dependencies becoming obsolete

::::