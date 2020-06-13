## Create App #2 ##

Delete all the files we don't need: 
* Hello.js
* Hello.css
* App.js
* App.css
* App.Test
* Logo.svg

Add Card tag to index.js: 
```javascript
ReactDOM.render( 
  <Card/>,	
  document.getElementById('root')
);
```
### Create Card.js ###

Create new file called Card.js in src folder. Then add the following to it, it is doing the function method as opposed to React class way: 
```javascript

import React from 'react';

const Card = () => {
	return(
	<div>
		<img alt='' src=""https://robohash.org/test?200x200"/>
		<div>
			<h2> Jane Doe</h2>
			<p>jane.doe@gmail.com</p>
		</div>
	</div>
	);
}
export default Card;

```
* Need to have alt properties for images
* Need to have React to read the JSX (even though not using class React way)
* Robohash website gives robot picture that varies based on last string in url. 
* ?200x200 dictates width and height of card- this is specific to Robohash site- I believe. 
* Can only return one element (div) with elements indented within. So can't add Title (h1) above div.
  
 ### Create multiple cards using index.js ###
 
 Add:
 ```javascript
 ReactDOM.render(
 <div>
  	<Card/>
  	<Card/>
  	<Card/>
</div>
,
document.getElementById('root')
);
```
### Styling ###

Add inline classname to 
* bg-light-greencolour dib = background color
* dib = display inline block (puts them in row)
* br3 = border 3
* pa3 = padding 3
* ma2 = margins 2
* grow = animation
* bw 2 =border width 2
* shadow-5 = shadow 5

```javascript
const Card = () => {
	return(
		<h1>
	<div className='bg-light-green dib br3 pa3 ma2 grow'>
		<img alt='' src="https://robohash.org/test?200x200"/>
		<div>
			<h2> Jane Doe</h2>
			<p>jane.doe@gmail.com</p>
		</div>
	</div>
	);
}
```

### Props to change names ###

Create new file called robots.js in src folder.

Add objects with robot details: 

```javascript
export const robots = {
	{ 
		id: 1,
		name: 'Rob Hamilton',
		username: 'RoboMan',
		email: 'roboman@gmail.com'
	},

	{ 
		id: 2,
		name: 'Luisa Hamilton',
		username: 'RoboWoMan',
		email: 'roboWoMan@gmail.com'
	},
	{ 
		id: 3,
		name: 'Elodie Hamilton',
		username: 'Eddie-bot',
		email: 'Edmund-bot@gmail.com'
	},
	{ 
		id: 4,
		name: 'Jack Hamilton',
		username: 'RoboMecahnic',
		email: 'mech-robo@gmail.com'
	},
	

}
```

Then add to index.js:

``` 
import robots from './'
```
