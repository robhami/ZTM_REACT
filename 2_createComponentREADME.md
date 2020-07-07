## Create App ##


### Overview of files ###
In index.js comment out:

```javascript
import App from './App';
```

because after NPM start in run terminal says: 

```javascript
Line 4:8:  'App' is defined but never used  no-unused-vars

```

After commenting out it compiles with no warnings

Don't need "Require" and then "Browserify". Like in other NPM packages. Can use import as long as its at top of script: 

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
```
This is because React has webpack that does the bundling/Browserify for us. 

React is a view library (little robot that does DOM manipulation for us). Can be used in places other than browser e.g. mobile apps. 

ReactDOM is for websites.

ReactNATIVE is for mobile.

React allows us to add specific css for each component (e.g. index.js has ./index.css). 
./ means its in same folder (i.e. src folder)

Service worker (not covered in this course) but they allow apps to work faster and potentially offline. Can comment out if you want but will leave it.

### index.js (with Hello World) ###
Code below says I want reactDOM package to render

```javascript
ReactDOM.render(
  <h1>Hello World</h1>,
  document.getElementById('root')
);

```

The Hello WORLD html was previously App. This refers to APP.js file that we commented out. Note no .js suffix because React assumes. js unless stated:

```javascript
import App from './App';
```

### App.js ###

In app.js class App extends Component:

A component must always render something. This is done by returning a HTML piece of website. 

```javascript
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
### index.js (connect to Hello.js)* ###

*the new App.js- created in next section)

Change import and html in index.js (note components e.g. Hello.js are capitalized): 

```javascript
// import App from './App';
import Hello from './Hello';
```

Then change rendered HTML: 

```javascript
ReactDOM.render(
  //<h1>Hello World</h1>,
  <Hello />,
	// <React.StrictMode>
  	//	<App />
  	// </React.StrictMode>,
  document.getElementById('root')
  
```

### Hello.js file ###

Need to create Hello.js file in src folder. This is replacing app.js. 

Add following to Hello.js file: 

```javascript
import React, {Component} from 'react';

class Hello extends React.Component {

	render() {

		return<h1>Hello World</h1>

	}

}

export default Hello;
```
Need export (last line of code above) to allow another file to use it. Using default means this file only exports one thing and that is the 'App' (or in this case "Hello.js").

To add more text/html, need to put in brackets around html after return as any more than one line causes issues:

```javascript
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

Can import Hello.css file by adding import line to Hello.js (originally App.js):

```javascript
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

```css
h1 {
	background: red;
}
```

### Tachhyons ###
Now install tachyons pacakge: 

```gitAttributes
Rob@RobPC MINGW64 ~/Documents/coding/Robofriends (master)
$ npm install tachyons  
```

This gives us classes we can use for modifying text (like Bootstrap). Need to import it into index .js:

```
import 'tachyons';
```

Add ClassName in Hello.js:

```javascript
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

### JSX ###
html is actually called JSX. React allows you to write HTML like syntax (JSX) in Javascript. 

Paradigm moves from separtion of concerns to separation of components with React. Just need to worry about .js and .css files. However html and js are mixed up but components are standalone.

Also React creates virtual DOM using html tags then converts it to real DOM, but only does whats needed so stays fast. 

Have to use className for div styling above because class is a reserved keyword in React JS for another purpose at start of code above (e.g. class Hello extends React.Component ). 

### Props ###
Arguments passed into React Components. Passed via HTML attributes. 
In index.js add greeting prop to <Hello/>:
By adding this line to index.js: 
 ** <Hello greeting={'Hello' + ' React Ninja'}/>, **
 
```javascript
ReactDOM.render(
  //<h1>Hello World</h1>,
  ** <Hello greeting={'Hello' + ' React Ninja'}/>, **
	// <React.StrictMode>
  	//	<App />
  	// </React.StrictMode>,
  document.getElementById('root')
);
```
Then call in Hello.js (previously App.js):

```javascript
render() {

	return (
	<div class='f1 tc'>
		<h1>Hello World</h1>
		<p>{this.props.greeting}</p>
	</div>

	)
}
```

 'this' object (i.e. <p> </p>) now has properties greeting in index.js

i.e. Hello React Ninja shows 

Note that React throws error due to unnecessary concatenation but will still run. 



### class are like functions ###

Can write class Hello as a function in Hello.js: 

```javascript
const Hello = (props) => {

	return (
	<div className="f1 tc">
	<h1>Hello World</h1>
	<p>{props.greeting}</p>
	</div>
	);
}
```
or
```
import React from 'react';
import './Hello.css'

function Hello(props){

		return(
		<div className='f1 tc'>
			<h1>Hello World</h1>
			<p>{props.greeting}</p>
		</div>
		)
	
};

export default Hello;

```
