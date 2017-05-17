# Events

- camelCase
- Pass a function as an expression

  ```
  ...
  <form className="w-100" onSubmit={handleSubmit}>
  ...
  ```
- prevent default browser behavior with `preventDefault`
- `e` is a synthetic event.

  ```
  function handleSubmit(e) {
    e.preventDefault();
    alert(
      "You submitted the form!"
    );
  }
  ```

  [React Docs: Handling Events](https://facebook.github.io/react/docs/handling-events.html)

## Events within a functional stateless component - Form Submit

[Try it](http://codepen.io/tripott/pen/NjzXJe?editors=0010)

```
const SignUp = props => {
  function handleSubmit(e) {
    e.preventDefault();
    alert(
      "You submitted the form!... well sort of.  this is just an alert message.  If this had been a real submit you would probably send the form's data to an api with an HTTP GET request using a library like xhr or fetch or isomorphic-fetch.. but what do I know?"
    );
  }

  return (
    <div>

      <article className="avenir mw7 center ph3 ph5-ns tc br2 pv5 bg-washed-blue dark-gray mb5">
        <h1 className="fw3 f1 lh-title mt0 mb3 black">
          Sign Up
        </h1>
        <h2 className="fw5 f4 lh-copy mt0 mb3">
          My Super App will solve your problem.  Sign up now.  If you are already a user, sign in.
        </h2>
        <p className="fw6 f5 mt0 mb3">
          My Super App is the best.
        </p>
        <form className="w-100" onSubmit={handleSubmit}>
          <div>
            <button
              className="f6 br-pill bg-dark-blue no-underline washed-blue ba b--dark-green grow pv2 ph3 dib mr3"
              type="submit"
            >
              Sign Up
            </button>
            <button
              className="f6 br-pill dark-blue no-underline ba grow pv2 ph3 dib"
              type="submit"
            >
              Sign In
            </button>

          </div>
        </form>
      </article>


    </div>
  );
};

ReactDOM.render(<SignUp />, document.getElementById("root"));
```

## Events within a functional stateless component - onClick

You can wire up a function to respond to a button's `onClick` event. Within the JSX that describes the button, provide an expression that refers the event handling function.  


[Try it](http://codepen.io/tripott/pen/eWKMZy?editors=0011)

```
const Cowbell = props => {
  function handleClick(e) {
    e.preventDefault();
    console.log("Gotta have that cowbell, baby.");
     console.log("e.target:", e.target);
     console.log("e.target.id:", e.target.id);
    console.log("e.target.innerHTML:", e.target.innerHTML);
  }

  return (
    <div>
      <ul className="list pl0 mt0 measure center">
        <li className="flex items-center lh-copy pa3 ph0-l bb b--black-10">
          <img
            className="w2 h2 w3-ns h3-ns br-100"
            src="http://stream1.gifsoup.com/view1/4392785/more-cowbell-o.gif"
          />
          <div className="pl3 flex-auto">
            <span className="f6 db black-70">More Cowbell</span>
            <span className="f6 db black-70">Bruce Dickenson, Incorprated</span>
          </div>
          <div>
            <button
              onClick={handleClick} id="5"
              className="f6 button-reset bg-white ba b--black-10 dim pointer pv1 black-60"
            >
              Click Me
            </button>
          </div>
        </li>

      </ul>
    </div>
  );
};

ReactDOM.render(<Cowbell />, document.getElementById("root"));
```

## Events within an ES6 Class

- When you define a component using an ES6 class, a common pattern is for an event handler to be a method on the class.
- You have to be careful about the meaning of this in JSX callbacks. In JavaScript, class methods are not bound by default. If you forget to bind the event handler and pass it to `onClick`, this will be undefined when the function is actually called.

[Try it](http://codepen.io/tripott/pen/RVJMzR)

```
class Cowbell extends React.Component {

  constructor(props) {
    super(props)

    this.state = {noise: ""}

    // class methods are not bound by default.
    //  Binding the event handler to the class with `this`
    this.handleCowbellHit = this.handleCowbellHit.bind(this);
  }

  handleCowbellHit () {
    this.setState(prevState => ({
      noise: prevState.noise + "donk "
    }));
  }


  render () {
    return (
    <div>
      <ul className="list pl0 mt0 measure center">
        <li className="flex items-center lh-copy pa3 ph0-l bb b--black-10">
          <img
            className="w2 h2 w3-ns h3-ns br-100"
            src="http://stream1.gifsoup.com/view1/4392785/more-cowbell-o.gif"
          />
          <div className="pl3 flex-auto">
            <span className="f6 db black-70">More Cowbell</span>
            <span className="f6 db black-70">Bruce Dickenson, Incorprated</span>
          </div>
          <div>
            <button
              onClick={this.handleCowbellHit} id="5"
              className="f6 button-reset bg-white ba b--black-10 dim pointer pv1 black-60"
            >
              Donk!
            </button>
          </div>
        </li>
        <p>{this.state.noise} </p>

      </ul>
    </div>
    )
  }
}

ReactDOM.render(<Cowbell />, document.getElementById("root"));
```
