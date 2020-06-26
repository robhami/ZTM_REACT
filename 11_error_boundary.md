## Error Boundary ##

If error in component there wasnt an easy way to fix it. 

Create file called ErroBoundary.js in Components:

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

