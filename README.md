# ZTM_REACT

Key principles: 

* Components separate & not dependant other parts of projects

* One way data flow- data loads from top to bottom. Only children know about changes not parents. 

* Virtual DOM- react bot creates virtual DOM which is JS object- then bot works in most optimum way

* Great Ecosystem- lots of material, apps and support

#### Create React App ####

Is the app that manages application development. 

To install globally on PC:

```gitattributes
Rob@Rob-Laptop MINGW64 ~
$ npm install -g create-react-app
C:\Users\rob.OSCDUBAI\AppData\Roaming\npm\create-react-app -> C:\Users\rob.OSCDUBAI\AppData\Roaming\npm\node_modules\create-react-app\index.js
+ create-react-app@3.4.1
added 98 packages from 46 contributors in 19.577s
```

To create application: 

```gitattributes
Rob@Rob-Laptop MINGW64 ~
$ create-react-app robofriends

```

To start React App: 

```
Rob@Rob-Laptop MINGW64 ~/robofriends (master)
$ npm start
```


In JSON file it points to React Scripts that do everything for you. 

```
{
  "name": "robofriends",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^4.2.4",
    "@testing-library/react": "^9.5.0",
    "@testing-library/user-event": "^7.2.1",
    "react": "^16.13.1",
    "react-dom": "^16.13.1",
    "react-scripts": "3.4.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  }
}
```

Eject is used to customize app.

There is also a package -lock.json file. It makes sure versions are correct. 

Also have a .gitignore file. It checks if anything needs to be ignored. 

Node modules also created. 

Public folder also created, that has inex.html, manifest.json that allows icon on desktop. 

Favicon.ico which is little icon that shows up at the top on the tab. 

Finally, we have src folder, where most stuff happens. index.js is main script file. It does a few script imports: 

```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

```

It also grabs element id root and ReactDOM renders the <APP/> (this is JSX), can change this to: (<h1>Hello World</h1>:


```
ReactDOM.render(
  <React.StrictMode>
   <h1>Hello World</h1>
  </React.StrictMode>,
  document.getElementById('root')
);

```
This show Hello World on screen instead of React landing page. 


In index.html: 

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <meta
      name="description"
      content="Web site created using create-react-app"
    />
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
    <!--
      manifest.json provides metadata used when your web app is installed on a
      user's mobile device or desktop. See https://developers.google.com/web/fundamentals/web-app-manifest/
    -->
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
    <!--
      Notice the use of %PUBLIC_URL% in the tags above.
      It will be replaced with the URL of the `public` folder during the build.
      Only files inside the `public` folder can be referenced from the HTML.

      Unlike "/favicon.ico" or "favicon.ico", "%PUBLIC_URL%/favicon.ico" will
      work correctly both with client-side routing and a non-root public URL.
      Learn how to configure a non-root public URL by running `npm run build`.
    -->
    <title>React App</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
    <!--
      This HTML file is a template.
      If you open it directly in the browser, you will see an empty page.

      You can add webfonts, meta tags, or analytics to this file.
      The build step will place the bundled scripts into the <body> tag.

      To begin the development, run `npm start` or `yarn start`.
      To create a production bundle, use `npm run build` or `yarn build`.
    -->
  </body>
</html>

```

There is just one div with id root- that gets all info to create landing page. This The no script file is just in case a browser isnt using javascript. 

Can edit index.js and cause it to show "hello World: 

```


```

Change to Babel JS to get colours 
