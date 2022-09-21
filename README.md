# Deploy React App to Firebase with GitHub Actions

## Requirements

- [Firebase Spark plan](https://firebase.google.com/pricing), no credit card required.
- [`npm` and `node` installed](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) on your machine.

## Steps

### 1. Create a New React App

To create the project:

```
npx create-react-app my-app
```

To test:

```
cd my-app
npm start
```

...and then visit http://localhost:3000

### 2. Setup Firebase Hosting

Follow the [Firebase docs to create a project](https://firebase.google.com/docs/web/setup#create-project).

[Install the Firebase CLI](https://firebase.google.com/docs/cli#install_the_firebase_cli).

Initialize the project with `firebase init hosting`, being sure to answer `Y` to the following:
> Set up automatic builds and deploys with GitHub?

Deploy with `firebase deploy --only hosting`.

## References
- [Create a new React app](https://reactjs.org/docs/create-a-new-react-app.html)
- [Get started with Firebase Hosting](https://firebase.google.com/docs/hosting/quickstart)
- [Using Firebase to deploy your React App](https://medium.com/@MinimalGhost/using-firebase-to-deploy-your-react-app-44ff90b2b0b6)
