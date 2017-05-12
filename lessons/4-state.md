# Lesson 4: State

## Student Prep

Review the following materials:

- https://facebook.github.io/react/docs/state-and-lifecycle.html
- https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Classes

## Intro to ES6 Classes

- To use state, you have to graduate up to an ES6 class that extends `React.Component`.

	** Stateless Functional Component	**
	```
	function Hello(props) {
  	return <h1>Hello, {props.name}. Is it me you are looking for?</h1>;
	}
	```

	** As an alternative to a stateless functional component you can use an ES6 Class **

	```
	class Hello extends React.Component {
  	render() {
    	return <h1>Hello, {this.props.name}. Is it me you are looking for?</h1>;
  	}
	}
	```

## Intro to state

- State is similar to props.
- It is private and fully controlled by the component.
- To set up a component with state you have to include a constructor method which is a special method for creating and initializing an object created with a class.
- The constructor method must accept in props as a parameter.
- Within the constructor, call the base constructor via `super`, passing props.
- Use `this.state` to initialize the state.  **The constructor is the only place where you can assign `this.state`.**
- If you aren't rendering the data to the UI, don't put the data into state.

```
class Hello extends React.Component {
	constructor(props) {
		super(props)
		this.state = {isCool: false};
	}

	render() {
		return (
      <div>
        <h1>Hello, {this.props.firstName} </h1>
        <h2>Are you cool? {this.state.isCool ? "yes": "no"}</h2>
			</div>
		)
	}
}

ReactDOM.render(
  <Hello firstName="Jeff"/>,
  document.getElementById('root')
)
```

## Try it.

- [React Simple ES6 class - State](http://codepen.io/tripott/pen/eWVjZX?editors=0010)

## Your turn: Creating a Component with an ES6 Class

- Using the following code pen as a template, [Fork this pen](http://codepen.io/tripott/pen/pPpXMo) to your account. Reviewing the settings for the template you will see it contains a reference to react and react-dom libraries and tachyons css.
- Create an ES6 Class component that displays an unordered list.  Each list item should contain the name of something such as a movie, album, actor, car, color, animal, etc.
- The data should be stored in state.
- When you are done, post the url to your codepen to the slack grind channel.  


## Correctly modifying state.

If the constructor is the only place where you can assign `this.state`, how do you set state throughout the lifecycle of the component?

0. Don't directly modify state.  `this.state.temperature = 90` is wrong. The only place where you can assign `this.state` is the constructor when you are initializing (setting up) the state for the first time in it's lifecycle.
0. Use `setState()` instead. Example: `this.setState({temperature: 90})`.
