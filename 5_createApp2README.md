## Create React App ##

### index.js ###
Delete  CardList.js add App.js instead : 
```
import App from './App';
```

### Build App.js ###

Need to copy and return ```<CardList robots={robots}/> ``` from index.js. Then import files: React, CardList, robots. 
Then import and add Search box.

```
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
### SearchBox.js ###

Create new Searbox.js file. Then add following: 

```
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
NB I commented out import robots and card in index.js because they showed as not being used. 

In App.js center everything by adding className="tc":

```
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

Need to define State info and rewrite function in class declaration method seen at start: 

```
import React, { Component } from 'react';
import CardList from './CardList';
import {robots} from './robots';
import SearchBox from './SearchBox';


const state = {
	robots: robots,
	searchfield: ''
}

class App extends Component {
	render () {
		return (
			<div className="tc">
			<h1>RoboFriends</h1>
			<SearchBox />
			<CardList robots={robots}/>
			</div>
		);
	}
}

export default App;
