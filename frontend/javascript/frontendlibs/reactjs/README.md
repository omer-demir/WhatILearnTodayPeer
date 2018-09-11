#### Intro
**JSX** stands for **_Javascript XML_**

for creating React Component we can use React.createClass
```javascript
var MyComponent = React.createClass({
    render: function(){
        return (
            <h1>Hello, world!</h1>
        );
    }
});
``` 

After creating component we need to render it

```javascript
ReactDOM.render(
    <MyComponent/>,
    document.getElementById('myDiv')
);
```

Every component can have properties in order to render dynamic data.
```javascript
var MyComponent = React.createClass({
    render: function(){
        return (
            <h1>Hello, {this.props.name}!</h1>
        );
    }
});

ReactDOM.render(<MyComponent name="Handsome" />, document.getElementById('myDiv'));
```

For creating component **render** function is only required. However there are additional methods.
##### LIFECYCLE METHODS

- *componentWillMount* – Invoked once, on both client & server before rendering occurs.
- *componentDidMount* – Invoked once, only on the client, after rendering occurs.
- *shouldComponentUpdate* – Return value determines whether component should update.
- *componentWillUnmount* – Invoked prior to unmounting component.

##### SPECS

- *getInitialState* – Return value is the initial value for state.
- *getDefaultProps* – Sets fallback props values if props aren’t supplied.
- *mixins* – An array of objects, used to extend the current component’s functionality.