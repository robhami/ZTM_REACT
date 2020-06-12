### Create App ###

In index.js comment out:
```
import App from './App';
```

because after NPM start in run terminal says: 

```
Line 4:8:  'App' is defined but never used  no-unused-vars

```

After commenting out it compiles with no warnings

Don't need "Require" and then "Browserify". Like in other NPM packages. Can use import as long as its at top of script: 

```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
```
This is because React has webpack that does the bundling for us. 

React is a view library (little robot that does DOM manipulation for us). Can be used in places other than browser e.g. mobile apps. 

ReactDOM is for websites.

ReactNATIVE is for mobile.

React allows us to add specific css for each component (e.g. index.js has index.css). ./ means its in same folder (i.e. src folder)

Service worker (not covered in this course) but they allow apps to work faster and potentially offline. Can comment out if you want but will leave it.

Code below says I want reactDOM package to render

```
ReactDOM.render(
  <h1>Hello World</h1>,
  document.getElementById('root')
);

```

The Hello WORLD html was previously App. This refers to APP.js file. Note no .js suffix because React assumes. js unless stated:

```
import App from './App';
```

In app.js class App extends Component:

A component must always render something.

```

import React from 'react';
import logo from './logo.svg';
import './App.css';
 
class App extends React.Component {
  render() {
    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <p>
            Edit <code>src/App.js</code> and save to reload.
          </p>
          <a
            className="App-link"
            href="https://reactjs.org"
            target="_blank"
            rel="noopener noreferrer"
          >
            Learn React
          </a>
        </header>
      </div>
    );
  }
}
 
export default App;

```
