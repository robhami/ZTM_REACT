## Create React App ##

### index.js ###
Delete  CardList.js add App.js instead : 

```javascript
import App from './App';
```

### Build App.js ###

Need to copy and return ```<CardList robots={robots}/> ``` from index.js. Then import files: React, CardList, robots. 
Then import and add Search box.

```javascript
import React from 'react';
import CardList from './CardList';
import {robots} from './robots';
import SearchBox from './SearchBox';

const App = () => {

	return(
		<div>
		<h1>RoboFriends</h1>
		<SearchBox />
		<CardList robots={robots}/>
		</div>
	)
}
export default App;
```
NB I commented out import robots and card in index.js because they showed as not being used. 

### SearchBox.js ###

Create new Searbox.js file. Then add following: 

```javascript
import React from 'react';

const SearchBox = () => {

	return (
		<div className="pa2">
			<input className="pa3 ba b--green bg-lightest-blue" type="search" placeholder="search robots" />
		</div>

		)
}

export default SearchBox;
```


In App.js center everything by adding className="tc":

```javascript
const App = () => {

	return(
		<div className="tc">
		<h1>RoboFriends</h1>
		<SearchBox />
		<CardList robots={robots}/>
		</div>
	)
}
```

### State ####

Because 1-way data flow components need to send data to their parent, so parent can communicate with other child components.

props are sent to functions and processed. These are pure functions/components. They don't need to know anything apart from what they receive and how to process them. 

In this case we need to update a component. 

State is required. State means adescription of your app. Its an object that describes your application.

The state in this app is the robots and whatever is entered in searchbox. We are able to change:
* What the robots array means (i.e. what gets displayed)
* Whatever is entered in the seachbox

Props are thing that come out of state. 

A parent feeds state into a child component
When child component receives a state its a property
The child can't change that property

### Rewrite App ###

Need to rewrite function in class declaration method seen at start and define State info in constructor: 

```javascript
import React, { Component } from 'react';
import CardList from './CardList';
import {robots} from './robots';
import SearchBox from './SearchBox';

class App extends Component {
	constructor () {
		super()
		this.state = {
			robots: robots,
			searchfield: ''
		}
	}

	render () {
		return (
			<div className="tc">
			<h1>RoboFriends</h1>
			<SearchBox />
			<CardList robots={this.state.robots}/>
			</div>
		);
	}

}

export default App;

```

* Now accessing robots from ```this.state.robots``` i.e. the constructor and not import lines at top. 
* Cardlist.js accepts "robots" as a prop whereas App.js accept it as a "state".
* App now owns state that includes "robots", so its allowed to change it.

### add onSearchChange function ###

Need to create a function can be called a different name (i.e. name does not cause anything). Everytime the input changes we get an event. This event is then console.logged. 

Can pass this function to searchBox tag by defining searchChange ```<SearchBox searchChange={this.onSearchChange}/>```

```
class App extends Component {
	constructor () {
		super()
		this.state = {
			robots: robots,
			searchfield: ''

		}
	}

	onSearchChange(event){
		console.log(event);


	}

		render () {
			return (
				<div className="tc">
				<h1>RoboFriends</h1>
				<SearchBox searchChange={this.onSearchChange}/>
				<CardList robots={this.state.robots}/>
				</div>
			);
		}

}

export default App;

```
Need to edit SearchBox.js
