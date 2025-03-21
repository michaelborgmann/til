# Deploying Web Frameworks on GitHub Pages

## Deploying Angular on GitHub Pages

To deploy an Angular project to GitHub Pages:

```
$ ng new angular-project
$ cd angular-project
$ ng add angular-cli-ghpages
$ ng deploy --base-href=/angular-project-repository/
```

## Deploying React (Vite) on GitHub Pages

Create a React project using Vite:

```
$ npm create vite@latest react-basic --template react
$ cd react-basic
$ npm install
```

1️⃣ Install gh-pages:
```
$ npm install gh-pages --save-dev
```
2️⃣ Add these lines to package.json under "scripts":
```
"predeploy": "npm run build",
"deploy": "gh-pages -d dist"
```
3️⃣ Update vite.config.js:
```
base: "/react-project-repository/",
```
4️⃣ Deploy:
```
npm run deploy
```

## Deploying Vue.js on GitHub Pages

Create a Vue project using Vite:
```
$ npm create vite@latest vue-project --template vue
$ cd vue-project
$ npm install
```

1️⃣ Install gh-pages:
```
npm install gh-pages --save-dev
```
2️⃣ Add these lines to package.json under "scripts":
```
"predeploy": "npm run build",
"deploy": "gh-pages -d dist"
```
3️⃣ Update vite.config.js:
```
base: "/vue-project-repository/",
```
4️⃣ Deploy:
```
npm run deploy
```
