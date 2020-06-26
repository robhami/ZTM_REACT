## Error Boundary ##

In previous versions of React, if error in component there wasn't an easy way to fix it. 

Create file called ErrorBoundary.js in Components:

```javascript
import React, { Component } from 'react';

class ErrorBoundary extends Component {
	constructor(props) {
		super(props);
		this.state = {	
				hasError: false
			}
		}

		componentDidCatch(error, info) {
			this.setState({hasError: true})

		}

		render () {
			if (this.state.hasError) {
				return <h1> Something went wrong </h1>
			}

			return this.props.children
		}
	
}

export default ErrorBoundary;
```

In App.js add to top: 

```javascript
import ErrorBoundary from '../Components/ErrorBoundary';
```
Wrap CardList in ErrorBoundary tags. 
```javascript
<Scroll>
    <ErrorBoundary>
      <CardList robots={filteredRobots}/>
    </ErrorBoundary>
</Scroll>
```
 Create error in CardList.js: 
 
 ```javascript
import React from 'react';
import Card from './Card';

const CardList = ({robots}) => {
	if (true) {
		throw new Error("NOOOOOO!");
	}
	return (
```

This will throw error details in Development mode. In production mode it will show page with "Something went wrong".


