### App.js Add scroll element and import ###

In App.js wrap cardList.js in Scroll tag. Plan to create a component called scroll that will allow scrolling but keep header at top. 
```javascript
return (
	<div className="tc">
	<h1 className="f1">RoboFriends</h1>
	<SearchBox searchChange={this.onSearchChange}/>
	<Scroll>
	<CardList robots={filteredRobots}/>
	</Scroll>
	</div>
	);
```

Also import:
```javascript
import Scroll from './Scroll'
```

### Create Scroll.js ###

Scroll is not a self closing component. It wraps. So need away to get it to render what's inside. 
Scroll can use children, as a way to render its children. This will show all the robots:

```javascript
import React from 'react';

const Scroll = (props) => {	
	console.log(props);
	return (
		props.children	
		);
};
export default Scroll;
```
Also the console.log shows all the props wrapped in Scroll: 

```
{children: {…}}
children:
$$typeof: Symbol(react.element)
key: null
props:
robots: (10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
__proto__: Object
ref: null
type: ({ robots }) => {…}
_owner: FiberNode {tag: 1, key: null, stateNode: App, elementType: ƒ, type: ƒ, …}
_store: {validated: true}
_self: App {props: {…}, context: {…}, refs: {…}, updater: {…}, onSearchChange: ƒ, …}
_source: {fileName: "C:\Users\Rob.000\Documents\coding\Robofriends\src\App.js", lineNumber: 59, columnNumber: 5}
__proto__: Object
__proto__: Object

```

If remove props.children and add <h1> only get the h1- not the CardList:

```javascript
import React from 'react';

const Scroll = (props) => {
	return (
		<h1>Hi</h1>
		);

};
export default Scroll;
```

Use double {} to add javascript expression returning an object that can have css styles

```javascript
import React from 'react';

const Scroll = (props) => {
	return (
		<div style={{overflowY:'scroll', border:'5px solid black', height: '500px'}}>
			{props.children}
		</div>
		);

};

export default Scroll;
```

overflowY makes element scrollable
must camelCase for JSX (e.g. overflowY)
