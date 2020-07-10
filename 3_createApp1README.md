## Create App #1 ##

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
  THIS HAS CHANGED NOW YOU CAN USE FRAGMENT: 
  
```
import React, { Fragment } from "react"

const Headings = props => {
  return (
    <Fragment>
      <h1>{props.title}</h1>
      <p>{props.subtitle}</p>
    </Fragment>
  )
}

```
Can also use <> to rep fragment: 
```
const Headings = props => {
  return (
    <>
      <h1>{props.title}</h1>
      <p>{props.subtitle}</p>
    </>
  )
}

```
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

Add inline classname to:
* tc = text center
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
export const robots = [
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
	

]
```

Because this is using export instead of export default this file could have multiple exports. For imports that aren't deafult you have to destructure 
when add import line to index.js. IE need curly brackets if not a default filename, also can put multiple filenames in here:

``` 
import { robots } from './robots'
```

Then change cards to link them to robot.js object number and associated property using properties curly brackets: 

```
ReactDOM.render(
 <div>
  	<Card id={robots[0].id} name={robots[0].name} email={robots[0].email}/>
  	<Card id={robots[1].id} name={robots[1].name} email={robots[1].email}/>
  	<Card id={robots[2].id} name={robots[2].name} email={robots[2].email}/>
  	<Card id={robots[3].id} name={robots[3].name} email={robots[3].email}/>
  	
</div>

,
document.getElementById('root')
);
```

Need card.js to accept parameters, put props as function input and {props.name} and {props.email} to h2 and p tags: 

```javascript
const Card = (props) => {
	return(
	
	<div className='bg-light-green dib br3 pa3 ma2 grow bw2 shadow-5'>
		<img alt='' src="https://robohash.org/test?200x200"/>
		<div>
			<h2> {props.name}</h2>
			<p> {props.email}</p>
		</div>
	</div>
	);

}

export default Card;

```

### Robo image dynamic using id ###

Use template string to change Robot based on id in Card.js file:



### Use variable to add props ###
Can add: 

``` const {name, email, id} =props;```

Then just need:

``` <h2> {name}</h2> ```

``` <p> {email}</p> ```

Code:

```javascript
<img alt='' src={`https://robohash.org/${props.id}?200x200`} />


import React from 'react';

const Card = (props) => {
	
	const {name, email, id} =props;
	return(
	

	<div className='tc bg-light-green dib br3 pa3 ma2 grow bw2 shadow-5'>
		<img alt='' src={`https://robohash.org/${props.id}?200x200`} />
		<div>
			<h2> {name}</h2>
			<p> {email}</p>
		</div>
	</div>
	);

}

export default Card;
```
An even cleaner way is add props to function input: 

```javascript
import React from 'react';

const Card = ({name, email, id} ) => {
	

	return(
	

	<div className='tc bg-light-green dib br3 pa3 ma2 grow bw2 shadow-5'>
		<img alt='' src={`https://robohash.org/${id}?200x200`} />
		<div>
			<h2> {name}</h2>
			<p> {email}</p>
		</div>
	</div>
	);

}

export default Card;

```
