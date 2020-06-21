

App.js is a smart component because it has state (a piece of data that describes our app). Whereas other components are just pure functions.

Method that come with React (called lifecycle hooks because they auto trigger when app gets loaded):

https://reactjs.org/docs/react-component.html

### Mounting ###

When click refresh the App.js component gets mounted into the document with the id of 'root'.

In index.js it is rendered to element with id root, this is known as mounting. 
```
ReactDOM.render(

	<App/>
,
document.getElementById('root')
);
```
This is in the index.html page:

```html
 <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
   
  </body>
</html>
```
#### Mounting ####
These methods are called in the following order when an instance of a component is being created and inserted into the DOM:

* constructor()
* static getDerivedStateFromProps()
* render()
* componentDidMount()

if missing will move to next one. 

#### Updating ####
- when component update on page (e.g. when you type in search box and robots list changes).

An update can be caused by changes to props or state. These methods are called in the following order when a component is being re-rendered:

* static getDerivedStateFromProps()
* shouldComponentUpdate()
* render()
* getSnapshotBeforeUpdate()
* componentDidUpdate()

#### Unmounting ####
This method is called when a component is being removed from the DOM:

* componentWillUnmount()

These lifecycle hooks run every time a component does something and come with React. Can put in class component and they'll automatically get triggered. You dont have to call them. 


```

If you are grabbing users via API from somewhere else on web. Need to change robots to empty array

```
class App extends Component {
	constructor () {
		super()
		this.state = {
			robots: [],
			searchfield: ''

		}
	}
```





https://jsonplaceholder.typicode.com/users
