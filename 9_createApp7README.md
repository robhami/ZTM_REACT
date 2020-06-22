

Lot of files in src file. Create folders to clean up: 

* Containers- for files with state in (App.js, App.css and also font file used in App.css)
* Components- for pure functions (Card, CardList, Scroll, SearchBox)

Need to change import lines as follows: 

In App.js: 

```
import CardList from '../Components/CardList';
import SearchBox from '../Components/SearchBox';
import Scroll from '../Components/Scroll';
```
../ means go up one level in folders. 

In index.js:

```
import App from './Containers/App';
```
Can do desstructuring with:
```
const { robots, searchfield } =this.state;
```
in the render section to stop repeating this.state:
```
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
  
