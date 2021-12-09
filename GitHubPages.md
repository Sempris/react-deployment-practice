# React App Deployment on GitHub Pages

## 1. Create an empty repository on GitHub.

- Create a repository named for example react-gh-pages.
- Empty means without a README.md file, a .gitignore file, a LICENSE file, or any other files.

## 2. Create a new React app on your computer.
```
$ create-react-app react-gh-pages
```
- This is the app you will deploy to GitHub Pages in step 7.
- You can either give the app the same name as your GitHub repository (i.e. react-gh-pages), or name them differently from one another (e.g. you can name your app app-123 and your GitHub Repository repo-456).
- This will create a new folder named react-gh-pages (or whatever you named your app) on your computer.

## 3. Install the gh-pages package as a "dev-dependency" of the app.
```
$ cd react-gh-pages
$ npm install gh-pages --save-dev
```
The commands shown in the following steps can all be issued from within the app's folder.

## 4. Add some properties to the app's package.json file.

At the top level, add a homepage property.

Define its value to be the string http://{username}.github.io/{repo-name}, where {username} is your GitHub username, and {repo-name} is the name of the GitHub repository you created in step 1.

Since my GitHub username is gitname and the name of my GitHub repository is react-gh-pages, you can add the following property:
```
//...
"homepage": "http://gitname.github.io/react-gh-pages"
```
In the existing scripts property, add a predeploy property and a deploy property, each having the values shown below:
```
"scripts": {
  //...
  "predeploy": "npm run build",
  "deploy": "gh-pages -d build"
}
```

## 5. Create a git repository in the app's folder.
```
$ git init
```
Initialized empty Git repository in C:/path/to/react-gh-pages/.git/

## 6. Add the GitHub repository as a "remote" in your local git repository.
```
$ git remote add origin https://github.com/gitname/react-gh-pages.git
```
This will make it so the gh-pages package knows where you want it to deploy your app in step 7.

It will also make it so git knows where you want it to push your source code (i.e. the commits on your master branch) in step 8.

## 7. Generate a production build of your app, and deploy it to GitHub Pages.
```
$ npm run deploy
```
That's it! Your app is now accessible at the URL you specified in step 4.