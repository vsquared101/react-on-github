This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

Steps to Deploy React App to Github Pages
-----------------------------------------

1. Create a new React app using below command:

projects > npx create-react-app test-react-deploy

Above command installs 'create-react-app' npm package and then creates a new React app named 'test-react-deploy' using it.
(This is the recommended way instead of installing create-react-app globally and then creating a project using it)

2. Once app is created navigate to the app folder and customize the code.

projects > cd test-react-deploy

Note: App created using create-react-app usually has git configured(if git is available on the local system).

3. Test/Run the app locally after making changes.

test-react-deploy > npm start

4. Create a new repository in Github:

<github_username>/<new_repo_name>

IMP: Make sure NO file is created by default inside the new repo(Not even README.md file)

5. Commit changes in local code base:

test-react-deploy > git add .
test-react-deploy > git commit -m "First commit"

6. Add remote repository to push the local React app code to.

test-react-deploy > git remote add origin <git_new_repo_url>
test-react-deploy > git remote -v  (lists all the remotes where the code is pushed to/fetched from for the current project folder)

test-react-deploy > git push origin master (pushes local React app code from 'master' branch to the remote repository's 'origin'  branch.)

7. Install gh-pages npm package.

test-react-deploy > npm install --save gh-pages

8. Update package.json file so that it has the 'homepage', 'predeploy', 'deploy' properties configured.
```
{
  "name": "test-react-deploy",
  "version": "0.1.0",
  "private": true,
  "homepage": "https://vsquared101.github.io/react-on-github/",
  "dependencies": {
    ...
  },
  "scripts": {
    ...
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  },
  "eslintConfig": {
    ...
  },
  "browserslist": {
    ...
  }
}
```
"homepage": The path where we want to host the application(value: "http://{username}.github.io/{repo-name}")  (MAKE SURE THE FORMAT FOR homepage is EXACTLY AS GIVEN HERE)
"predeploy": This command helps bundle the React App.(creates the 'build' folder that is to be deployed on github pages)
"deploy": publishes the bundle created to github('build' folder is deployed to github pages)

9. Optionally we can commit current code to git using > git add . and > git commit -m "Second commit"

10. Navigate to the URL configured in the "homepage" property. If everything went well before this step the application homepage should be displayed.

IMP: We may face issues with navigation if we use BrowserRouter from the react-router-dom module. Possible solutions involve using HashRouter instead of BrowserRouter.


