## Create App #2 ##

Delete all the files we don't need: 

Hello.js
Hello.css
App.js
App.css
App.Test
Logo.svg

Add Card tag to index.js: 

```
ReactDOM.render(
 
  <Card/>,
	
  document.getElementById('root')
);
```
### Create Card.js ###

Create new file called Card.js Then add the following to it, it is doing the function method as opposed to React class way: 

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

* Need tp have alt properties for images
* Need to have React to read the JSX (even though not using class React way)
* Robohash website gives robot picture that varies based on last string in url. 
* ?200x200 dictates width and height of card- this is specific to Robohash site- I believe. 
* can only return one element (<div>) with elements indented within. So can't add Title (h1) above div.
  
 ### Create multiple using index.js ###
 
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

