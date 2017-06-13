# React Test 1

## Quiz

0. True or False.  You can define a component with a JavaScript function?
0. In one word, what are the smallest building blocks of React apps?
0. In one word, what syntax would you use to describe what the UI should look like?
0. In one word, what are React components made of?
0. In one word, what is the name of the object used to pass JSX attributes and data into a component as an argument?
0. True or False.  When creating a React component, you have to use a class rather than a function if you wish to pass data into the component.
0. In two words, what do you use to you embed a JavaScript expression in JSX?
0. True or False. When an update to the DOM is needed, react DOM replaces the entire DOM updates to bring the DOM to the desired state.
0. In one word, what is used to break the user interface into smaller pieces?
0. True or False. Start components with a capital letter.
0. True or False. Components can optionally return multiple root elements.
0. True or False. A component can be composed of smaller components.
0. True or False. "pure" functions do not attempt to change their inputs, and always return the same result for the same inputs.
0. True or False.  The function below is not "pure":
  ```
  function totalsWithTax(x, y) {
    return (x * y) + 10
  }
  ```
0. True or False.  A React component must never modify it's own props.
0. True or False. Defining a component as a class rather than a function allows the ability to use additional features such as local state and lifecycle hooks.  
0. Review the following code within this CodePen: http://codepen.io/tripott/pen/aWErJP?editors=0011
  - Fork the pen to your CodePen account.  
  - Modify the component so that it accepts and displays a name within the `h2` tag.
  - Run the `display()` function in the console to display the component.
    ```
    function Hello() {
      return (
        <div>
          <h1>Hello, world!</h1>
          <h2>My name is .</h2>
        </div>
      );
    }

    function display() {
      ReactDOM.render(
        <Hello />,
        document.getElementById('root')
      );
    }
  ```
