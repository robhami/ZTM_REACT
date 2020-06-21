

App.js is a smart component because it has state (a piece of data that describes our app). Whereas other components are just pure functions.

Method that come with React (called lifecycle hooks because they auto trigger when app gets loaded):

https://reactjs.org/docs/react-component.html

### Mounting ###

When click refresh the App.js component gets mounted into the document with the id of 'root'.

In index.js it is rendered to element with id root, this is known as mounting. 
```
ReactDOM.render(

	<App/>
,
document.getElementById('root')
);
```
This is in the index.html page:

```html
 <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
   
  </body>
</html>
```
#### Mounting ####
These methods are called in the following order when an instance of a component is being created and inserted into the DOM:

* constructor()
* static getDerivedStateFromProps()
* render()
* componentDidMount()

if missing will move to next one. 

#### Updating ####
- when component update on page (e.g. when you type in search box and robots list changes).

An update can be caused by changes to props or state. These methods are called in the following order when a component is being re-rendered:

* static getDerivedStateFromProps()
* shouldComponentUpdate()
* render()
* getSnapshotBeforeUpdate()
* componentDidUpdate()

#### Unmounting ####
This method is called when a component is being removed from the DOM:

* componentWillUnmount()

These lifecycle hooks run every time a component does something and come with React. Can put in class component and they'll automatically get triggered. You dont have to call them. 


If you are grabbing users via API from somewhere else on web. Need to change robots to empty array

```
class App extends Component {
	constructor () {
		super()
		this.state = {
			robots: [],
			searchfield: ''

		}
	}
```

### componentDidMount() example ###

Can add this and it will console log when app opens, showing that component mounted:

```
componentDidMount() {

		console.log('check');

	}

```
Can set state to robots from robots.js file when it mounts, need to do this because array is now set to empty: 

```
componentDidMount() {

		this.setState({ robots: robots });

	}
	
```

Add console.logs to see what parts of the code run when: 

```
import React, { Component } from 'react';
import CardList from './CardList';
import {robots} from './robots';
import SearchBox from './SearchBox';
import './App.css';

class App extends Component {
	constructor () {
		super()
		this.state = {
			robots: [],
			searchfield: ''

		}
		console.log('constructor');
	}


	componentDidMount() {

		this.setState({ robots: robots });
		console.log('componentDidMount');

	}



	onSearchChange = (event) =>{

		this.setState({ searchfield: event.target.value})
		
	}

		render () {
			
			const filteredRobots = this.state.robots.filter(robot => {

			return robot.name.toLowerCase().includes(this.state.searchfield.toLowerCase())
			
			})
				console.log('render');
			return (
				<div className="tc">
				<h1 className="f1">RoboFriends</h1>
				<SearchBox searchChange={this.onSearchChange}/>
				<CardList robots={filteredRobots}/>
				</div>
			);
		}

}

export default App;

```
Console displays this order (same as  

* constructor
* render
* componentDidMount
* render

This is same order as given in React readme notes (i.e. above under Mount heading):

* constructor()
* static getDerivedStateFromProps()
* render()
* componentDidMount()

Why did render run again? Because state gets updated in componentDidMount. Everytime state changes - go through updating lifecycle (see Updating heading above) and runs render again. It goes from empty array to robots list, render gets rerun and the virtual DOM notices and adds the robots.

Can now pull from API as follows, remove ```import {robots} from './robots';``` then do : 

```
componentDidMount() {
	fetch ('https://jsonplaceholder.typicode.com/users')
		.then(response =>{
				return response.json();

	})

	.then(users=> {
			this.setState({ robots: users });
			console.log('componentDidMount');
	});
}
```
Fetch is an inbuilt method in the browser:
```
window.fetch;
ƒ fetch() { [native code] }
```
Can add loading message when delayed: 
```
render () {
			
			const filteredRobots = this.state.robots.filter(robot => {

					return robot.name.toLowerCase().includes(this.state.searchfield.toLowerCase())
			
					})
			
			if (this.state.robots.length ===0) {

				return <h1>Loading</h1>
			} else {

			return (
				<div className="tc">
				<h1 className="f1">RoboFriends</h1>
				<SearchBox searchChange={this.onSearchChange}/>
				<CardList robots={filteredRobots}/>
				</div>
			);
		}
	}
```
https://jsonplaceholder.typicode.com/users
