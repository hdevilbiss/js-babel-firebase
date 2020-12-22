# JavaScript, Babel, and Firebase

This project uses the [Babel CLI](https://babeljs.io/docs/en/babel-cli) for transpiling vanilla ES6 into browser-compatible code, and [Google Firebase](https://firebase.google.com/) for hosting and deployment.

## Using the Project

1. Clone the repository.
1. Remove the .git folder: `rm -rf .git`
1. Initiate a repository locally: `git init`
1. On GitHub or similar, create your own git repo to serve as the remote for your project.
1. Within the local copy, add the new repository as the remote url: `git remote add origin <new-repo-url>`
1. Follow the steps below to setup the Node dependencies and setup hosting and deployment to Firebase.

## Node Prerequisite

It is assumed that you have Node installed either on your machine and can use Node commands from the terminal.

For example: I have a Windows 10 computer. I used [nvm](https://github.com/nvm-sh/nvm) on my [Windows Linux Subsystem](https://docs.microsoft.com/en-us/windows/wsl/install-win10) to install Node, and run all `npm` commands from an Ubuntu subsystem in the VSCode terminal.

## Getting Started with Babel

> Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older browsers

Source: [babeljs.io](https://babeljs.io/docs/en)

1. Run **`npm i`** to install `node_modules` from `package-lock.json`.
1. Save ES2015+ JavaScript under the `src` folder, which is where Babel looks for JS files to compile.
1. Alternatively, edit the `build` and `watch` scripts in `package.json` to direct Babel to your JS folder.
1. Use **`npm run build`** to manually transpile JavaScript to the `public` folder.
1. Auto-transpile every time you save an update using `npm run watch`.

## Deployment with Firebase

Firebase is a Google Backend as a Service (BaaS) provider which makes deploying JavaScript projects easy and [free-until-you-get-big](https://firebase.google.com/pricing/).

### Shout-out

📹🔥 Thanks to **[Fireship](https://www.youtube.com/watch?v=q5J5ho7YUhA)** for providing **informative tutorials on YouTube**

I would recommend you follow the Fireship tutorial, because it'll get you setup with user authentication with Google, a NoSQL database, and database rules.

However, if you are only interested in hosting static files, then you can checkout the main steps needed for **hosting and deployment in the [Wiki section of this repo](https://github.com/hdevilbiss/js-babel-firebase/wiki/Deploy-with-Firebase)**.

You can also checkout the [Firebase web setup documentation](https://firebase.google.com/docs/web/setup).

### Firebase Documentation

Visit the [official documentation](https://firebase.google.com/docs/) from Firebase.
