## Create App ##


### Overview of files ###
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
This is because React has webpack that does the bundling/Browserify for us. 

React is a view library (little robot that does DOM manipulation for us). Can be used in places other than browser e.g. mobile apps. 

ReactDOM is for websites.

ReactNATIVE is for mobile.

React allows us to add specific css for each component (e.g. index.js has index.css). ./ means its in same folder (i.e. src folder)

Service worker (not covered in this course) but they allow apps to work faster and potentially offline. Can comment out if you want but will leave it.

### index.js just Hello World ###
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
### App.js ###

In app.js class App extends Component:

A component must always render something. This is done by returning a HTML piece of website. 

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
### index.js ###

Change import and html in index.js (note components e.g. Hello.js are capitalized): 

```
// import App from './App';
import Hello from './Hello';
```

Then change rendered HTML: 

```
ReactDOM.render(
  //<h1>Hello World</h1>,
  <Hello />,
	// <React.StrictMode>
  	//	<App />
  	// </React.StrictMode>,
  document.getElementById('root')
  
```

### Hello.js file ###

Need to create Hello.js file in src folder.

Add following to Hello.js file: 

```
import React, {Component} from 'react';

class Hello extends React.Component {

	render() {

		return<h1>Hello World</h1>

	}

}

export default Hello;
```
Need export to allow another file to use it. Using default means this file only exports one thing and that is the 'App' (ot maybe "Hello").

To add more text/html, need to put in brackets around html after return:

```
import React, {Component} from 'react';

class Hello extends React.Component {

	render() {

		return (
		<div>
			<h1>Hello World</h1>
			<p>Welcome to React</p>
		</div>
	
		)
	}

}

export default Hello;
```

### css.file ###

Can import Hello.css file by adding import line:
```
import React, {Component} from 'react';
import './Hello.css'
class Hello extends React.Component {

	render() {

		return (
		<div>
			<h1>Hello World</h1>
			<p>Welcome to React</p>
		</div>
	
		)
	}

}

export default Hello;
```

Then create Hello.css in src folder and add css as follows: 

```
h1 {
	background: red;
}
```

### Tachhyons ###
Now install tachyons pacakge: 

```
Rob@RobPC MINGW64 ~/Documents/coding/Robofriends (master)
$ npm install tachyons  
```

This gives us classes we can use for modifying text (like Bootstrap). 

```
import React from 'react';
import './Hello.css'
class Hello extends React.Component {

	render() {

		return (
		<div className='f1 tc'>
			<h1>Hello World</h1>
			<p>Welcome to React</p>
		</div>
	
		)
	}

}

export default Hello;
```

html is actually called JSX. React allows you to write HTML like syntax (JSX) in Javascript. 

Paradigm moves from separtion of concerns to separation of components with React. Just need to worry about .j and .css files. 

Also React creates virtual DOM using html tags then converts it to real DOM, but only does whats needed so stays fast. 

Have to use className for div styling above because class is a reserved keyword in React JS for another purpose at start of code above (e.g. class Hello extends React.Component ). 

#### Props ####

In index.js add greeting prop to <Hello/>:

```
ReactDOM.render(
  //<h1>Hello World</h1>,
  <Hello greeting={'Hello' + ' React Ninja'}/>,
	// <React.StrictMode>
  	//	<App />
  	// </React.StrictMode>,
  document.getElementById('root')
);
```
Then add in hello.js:

```render() {

		return (
		<div class='f1 tc'>
			<h1>Hello World</h1>
			<p>{this.props.greeting}</p>
		</div>
	
		)
	}
```
 this object - hello has properties greeting in index.js

Can write class Hello as a function: 
```
const Hello = (props) => {

	return (
	<div className="f1 tc">
	<h1>Hellow World</h1>
	<p>{props.greeting}</p>
	</div>
	);
}
```
