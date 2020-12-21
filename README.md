# My freeCodeCamp Projects

5 projects completed for the [freeCodeCamp](https://www.freecodecamp.org/learn) JavaScript certificate.

This project uses the [Babel CLI](https://babeljs.io/docs/en/babel-cli) for transpiling vanilla ES6 into browser-compatible code, and [Google Firebase](https://firebase.google.com/) for hosting and deployment.

## Using the Project

1. Clone the repository.
1. Remove the .git folder: `rm -rf .git`
1. Initiate a repository locally: `git init`
1. On GitHub or similar, create your own git repo to serve as the remote for your project.
1. Within the local copy, add the new repository as the remote url: `git remote add origin <new-repo-url>`
1. Follow the steps below to setup the Node dependencies and setup deployment to Firebase.

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

📹🔥 Thanks to **[Fireship](https://www.youtube.com/watch?v=q5J5ho7YUhA)** for providing **informative tutorials on YouTube**.

1. Install firebase-tool globally. `npm install -g firebase-tools`
1. Check firebase was installed. `firebase --version`
1. Login to your Firebase account. `firebase login`
1. You will be redirected to login to your Google account.
1. Logout of your Firebase account if needed. `firebase logout`
1. Initiate a Firebase project in your VSCode workspace. `firebase init`
    - Enable options with the space bar, select them by entering. Finish selecting all options.
    - Choose to deploy from `public`.
1. If you are using emulators for hosting, then you can start the preview with `firebase emulators:start`
1. Alternatively, you can use the `firebase serve` command.
1. Deploy your app to Firebase. `firebase deploy`

🔗 Link to the [Firebase console](https://console.firebase.google.com/u/0/)

### Easy Continuous Integration with Firebase

During the `firebase init` session, you will have the option to choose whether you want to auto-deploy on merge to the main branch and/or on pull request. As long as you want your app to visible live from the web, you should do it! Get your feet wet with CI!

This initiation step will setup two workflow documents in a `/.github` folder, which are in YAML format.

You can specify build steps which run automatically with a GitHub Action; this is a great time to auto-transpile your ES6.

Here is an example of how this document will look. Please take note of the `run` step: **`npm run i && npm run build`**, which first installs node_modules, then runs the build command specified in the `package.json` file.

If you also need to build LESS or SASS, you can add them to your `build` command.

```yaml
jobs:
    build_and_preview:
        runs-on: ubuntu-latest
        steps:
            - uses: actions/checkout@v2
            - run: npm run i && npm run build
            - uses: FirebaseExtended/action-hosting-deploy@v0
              with:
                  repoToken: "${{ secrets.GITHUB_TOKEN }}"
                  firebaseServiceAccount: "${{ secrets.FIREBASE_SERVICE_ACCOUNT_APP_NAME }}"
                  projectId: app-name
              env:
                  FIREBASE_CLI_PREVIEWS: hostingchannels
```

### Firebase Documentation

Visit the [official documentation](https://firebase.google.com/docs/) from Firebase.
