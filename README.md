# Deploy React App to Firebase with GitHub Actions

## Requirements

- [Firebase Spark plan](https://firebase.google.com/pricing), no credit card required.
- [`npm` and `node` installed](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) on your machine.

## Steps

### 1. Create a New React App

- To create the project:

    ```
    npx create-react-app my-app
    ```

- To test:

    ```
    cd my-app
    npm start
    ```

    ...and then visit http://localhost:3000 to test.

- At this point, you can [create a new GitHub repo](https://docs.github.com/en/get-started/quickstart/create-a-repo#create-a-repository) and follow the steps in the repo to push an existing directory. Your repo should look like the [`step-1-complete` branch](https://github.com/a-mabe/actions-firebase-workshop/tree/step-1-complete).

### 2. Setup Firebase Hosting

- Now you can move the ReactJs files into their own [`web-app` directory](https://github.com/a-mabe/actions-firebase-workshop/commit/2368e9632810c78319e15f57d2e13dae292bfca9).

- Follow the [Firebase docs to create a project](https://firebase.google.com/docs/web/setup#create-project).

- [Install the Firebase CLI](https://firebase.google.com/docs/cli#install_the_firebase_cli).

- Initialize the project with `firebase init hosting`, answering the questions as follows:
    > What do you want to use as your public directory? **web-app/build**
    
    > Configure as a single-page app (rewrite all urls to /index.html)? **y**
    
    > Set up automatic builds and deploys with GitHub? **y**
    
    > For which GitHub repository would you like to set up a GitHub workflow? (format: user/repository) **<Repo that you set up in Step 1>**
    
    > Set up the workflow to run a build script before every deploy? **y**
    
    > What script should be run before every deploy? **npm install && npm run build**
    
    > Set up automatic deployment to your site's live channel when a PR is merged? **y**
    
    > What is the name of the GitHub branch associated with your site's live channel? **<Name of your repo's branch>**

- Deploy with `firebase deploy --only hosting`.

- Push your changes to GitHub. Your repo should look like the [`step-2-complete` branch](https://github.com/a-mabe/actions-firebase-workshop/tree/step-2-complete).

### 3. Modify Workflows

- Two workflows were automatically created when Firebase hosting was initialized: `firebase-hosting-merge.yml` and `firebase-hosting-pull-request.yml`. Modify these files to add the working directory and node setup:

    Add working directory to each `.yml`:
    ```
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: web-app
    ```
    
    Add node setup to each `.yml`:
    ```
    - uses: actions/checkout@v2

    - uses: actions/setup-node@v3
        with:
            node-version: 16
    ```
    
    Repo should resemble the [`step-3-complete` branch](https://github.com/a-mabe/actions-firebase-workshop/tree/step-3-complete).

## References
- [Create a new React app](https://reactjs.org/docs/create-a-new-react-app.html)
- [Get started with Firebase Hosting](https://firebase.google.com/docs/hosting/quickstart)
- [Using Firebase to deploy your React App](https://medium.com/@MinimalGhost/using-firebase-to-deploy-your-react-app-44ff90b2b0b6)
