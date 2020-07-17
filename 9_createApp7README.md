## Clean up project ##

Lot of files in src file. Create folders to clean up: 

* Containers- for files with state in (App.js, App.css and also font file used in App.css)
* Components- for pure functions (Card, CardList, Scroll, SearchBox)

Need to change import lines as follows: 

In App.js: 

```javascript
import CardList from '../Components/CardList';
import SearchBox from '../Components/SearchBox';
import Scroll from '../Components/Scroll';
```
../ means go up one level in folders. 

In index.js:

```javascript
import App from './Containers/App';
```
Can do desstructuring in App.js with:
```javascript
const { robots, searchfield } =this.state;
```
So in the render section to stop repeating "this.state" i.e. delete "this.state" anytime it appears before "robots" or "searchfield":
```javascript
render () {
		const { robots, searchfield } =this.state;
		const filteredRobots = robots.filter(robot => {

				return robot.name.toLowerCase().includes(searchfield.toLowerCase())

				})

		if (robots.length ===0) {

			return <h1>Loading</h1>
		} else {

		return (
			<div className="tc">
			<h1 className="f1">RoboFriends</h1>
			<SearchBox searchChange={this.onSearchChange}/>
			<Scroll>
			<CardList robots={filteredRobots}/>
			</Scroll>
			</div>
		);
	}
}
  ```
  
Can also tidy this, i.e. if robots.length is false (same as 0) and change if/else to tenary: 

```
return !robots.length ?
		<h1>Loading</h1> :
	(
		<div className="tc">
		<h1 className="f1">RoboFriends</h1>
		<SearchBox searchChange={this.onSearchChange}/>
		<Scroll>
		<CardList robots={filteredRobots}/>
		</Scroll>
		</div>
	);
	
```

Ctrl c in terminal, then type: "npm run build". This creates all files in optimized style. So can take all in build folder and put it somewhere. 
