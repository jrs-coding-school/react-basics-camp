# Lesson 5: Component lifecycle

There are special events in the life of a component.  When a component is rendered to the DOM is one such event.  This is know as "mounting".  After the component is initially rendered, the `ComponentDidMount()` method is called by React.  When the portion of the DOM holding the component is removed, the component unmounts and the `ComponentWillUnmount()` method is called.

>  `ComponentDidMount()` and `ComponentWillUnmount()` are known as "lifecycle hooks".

`ComponentDidMount()` is a good point in the component's lifecycle to grab some data and update the state with the data. `ComponentWillUnmount()` is a good place to free up resources taken by the components when the component is unmounted and destroyed.

## Try it

- Open the following codepen: [React Simple ES6 class-setState()](http://codepen.io/tripott/pen/YVeMQL?editors=0011)
- Open the codepen console
- Notice the `console.log()` messages within the code
- Notice the order in which they are displayed in the codepen console.

##  Using a function to `setState()`

- React may batch multiple `setState()` calls into a single update for performance.
- Because `this.props` and `this.state` may be updated asynchronously, you should not rely on their values for calculating the next state.
- Use a second form of `setState()` that accepts a _function_ rather than an object. That function will receive the previous state as the first argument, and the props at the time the update is applied as the second argument.

## Try it

- [React  Simple ES6 class - setState() - calculating next state with fn()](http://codepen.io/tripott/pen/eWMWdG?editors=0011)

## Pass Data Down

- A component may choose to pass its state down as props to its child components.

## Try it

- [React  Simple ES6 class - pass data down](http://codepen.io/tripott/pen/KmovdL?editors=1010)

## Your Turn: Pass state as props to children.

- Use the previous example for guidance.
- [Fork this codepen template](http://codepen.io/tripott/pen/YVLNBG?editors=0011).
- [Sign In/ Sign Up](https://www.wunderground.com/weather/api) for a Weather Underground API developer account.
- [Navigate back to the api docs and obtain an API Key](https://www.wunderground.com/weather/api)
- [Get Tide Data from WU API](https://www.wunderground.com/weather/api/d/docs?d=data/tide) and make it available within your component using state.  Perform an HTTP GET to the follwing url.  Once retrieved  set the response data as state using `setState()`.

	```
	http://api.wunderground.com/api/your api key goes here/tide/q/SC/Charleston.json
	```
- Within the parent `TideSummary` component's `render()` function, map over the `tideSummary` array. For each object in the array,  paint a series of `TideSummaryItem` child components to the user interface.
- Pass the following data as props to each `TideSummaryItem`:
	- `tideSummary.date.pretty` Ex: "8:09 PM EDT on May 12, 2017"
	- `tideSummary.data.height` Ex: "0.28 ft"
	- `tideSummary.data.type` Ex: "Low Tide"
