## Create App 2 ##

### CardList.js ###
Create card list and cut robot elements from index.js to be rendered there and add {robots} as destructured input to CardList function: 

```javascript
import React from 'react';
import Card from './Card';

const CardList = ({robots}) => {
	return (

	 <div>
	  	<Card id={robots[0].id} name={robots[0].name} email={robots[0].email}/>
	  	<Card id={robots[1].id} name={robots[1].name} email={robots[1].email}/>
	  	<Card id={robots[2].id} name={robots[2].name} email={robots[2].email}/>
	  	<Card id={robots[3].id} name={robots[3].name} email={robots[3].email}/>
	  	
	</div>

		);


}

export default CardList;
```
### In index.js:###

Import Cardlist and change index.js to just render CardList: 
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
// import App from './App';
import Card from './Card';
import CardList from './CardList';
import * as serviceWorker from './serviceWorker';
import 'tachyons';
import { robots } from './robots';

ReactDOM.render(

	<CardList robots={robots}/>
,
document.getElementById('root')
);

serviceWorker.unregister();

```
### In CardList.js loop extract from robot object/array ###

Create function that maps (loops) through objects and extracts index (i) and uses this to pull each index (this is because index is second parameter of map (https://www.w3schools.com/jsref/jsref_map.asp): 

```javascript
import React from 'react';
import Card from './Card';
const CardList = ({robots}) => {
	const cardArray = robots.map((user, i) => {
		return (
		<Card 
		key={robots[i].id} 
		id={robots[i].id} name={robots[i].name} email={robots[i].email}
		/>
		)
	})	
	return (
	 <div>
	  	{cardArray}	
	</div>

	);
}

export default CardList;


```
Above- have to assign a **key prop** to each child in array (e.g. Robots). Otherwise if card get deleted entire DOM has to change as React won't have an identifier. This overworks DOM. id is a good choice for a key because it doesn't change, this is better if things get moved.  

Below-Can also just add all cardArray code into a return and not require const cardArray:

```javascript
import React from 'react';
import Card from './Card';

const CardList = ({robots}) => {
	return (
		
		<div>
			{
				robots.map((user, i) => {
					return(
						<Card 
						key={robots[i].id} 
						id={robots[i].id} name={robots[i].name} email={robots[i].email}
						/>
					);
				})
			}
		</div>

	);
}

export default CardList;

```
