## Create React App ##

### index.js ###
Delete  CardList.js add App.js instead : 
```
import App from './App';
```

### Build App.js ###

Need to copy and return ```<CardList robots={robots}/> from index.js```. Then import files: React, CardList, robots. 
Then import and add Search box.

```
import React from 'react';
import CardList from './CardList';
import {robots} from './robots';
// import SearchBox from './SearchBox';

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
