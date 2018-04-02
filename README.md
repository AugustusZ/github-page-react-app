# How to deploy a react app on github pages

Given your repo where your working react app is on, let's say, `working-react-app` branch, and all the following steps (except step 1) happen on this branch.

## Configure for the first time

1.  Create a new branch `gh-pages` on your repo page (from whichever branch you want because the whole `gh-pages` branch content will be later replaced with you built app anyway) and then go to **Settings** | **Options** | **GitHub Pages** to make sure the `gh-pages` branch is selected as the source:
    ![](/images/source.png)

1.  Install `gh-pages`:

    ```bash
    npm install --save-dev gh-pages
    ```

1.  Add `homepage` field in your `package.json` indicating your GitHub Pages URL for your repo:

    ```json
    {
      // ...
      "homepage": "http://yourusername.github.io/your-react-repo-name/"
      // ...
    }
    ```

    e.g. for this repo, it is

    ```json
    {
      // ...
      "homepage": "http://augustusz.github.io/github-page-react-app/"
      // ...
    }
    ```

1.  Then, add the following script in your `package.json`

    ```json
    {
      // ...
      "scripts": {
        // ...
        "predeploy": "npm run build",
        "deploy": "gh-pages -d build"
      }
    }
    ```

Now you should have all the confgiration your need for the deployment.

## Deploy

After configure for the first time, (or every time you update your app code and you want to depoly it) simply run

```bash
npm run deploy
```

Input your username and password.

When you see `Published` logged, the depolyment is done. You should see your deployed app on the `homepage` URL now.

## Reference

https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#github-pages
