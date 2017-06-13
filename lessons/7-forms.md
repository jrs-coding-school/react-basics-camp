# Forms

- Form elements keep internal state
- A 'normal' html / non-React form will browse to a new page when submitted.  This is typically not done with a React form.
- Use a JavaScript function to handle the submit including the data associated with the form.
- Use "controlled components" to track the data within each of the form elements as the user types in data.
- Data within the form elements are tracked in state.
- Form elements like `<input>` maintain their own state.
- State is updated as the user interacts with the form element.

- For example, within a form we have an `<input>` text control element, use the `value` attribute to tie a value within state to the control.  When the value changes in state, the value will be updated in the control.

- Use the `onChange` event within the control to provide a function that handles the change.  Every time a user types in text, the function will be invoked and the current value will be updated in state.

  ```
  constructor(props) {
   super(props);
   this.state = {
     name: "",
     amount: 0,
     unit: "mg",
   }
  this.handleNameChange = this.handleNameChange.bind(this);
  ...
  }

  handleNameChange(event) {
    this.setState({ name: event.target.value });
  }

  ...
  render() {
    return (
      ... code omitted for brevity ...
      <input
        className="pa2 input-reset ba bg-transparent w-100 measure"
        type="text"
        id="name"
        size="100"
        value={this.state.name}
        onChange={this.handleNameChange}
      />
    ...
  ```

> "Since the value attribute is set on our form element, the displayed value will always be `this.state.value`, making the React state the source of truth. Since `handleNameChange` runs on every keystroke to update the React state, the displayed value will update as the user types."

- [Try Me: React Forms Simple Controlled Component](http://codepen.io/tripott/pen/EmRMEd?editors=0011)

## Your turn: adding controlled inputs

- [Fork this codepen: React Forms Simple Controlled Component](http://codepen.io/tripott/pen/EmRMEd?editors=0011).
- Similar to the **name** `<input>` element, add another element named **instructions** that tracks patient instructions for the medication.  
- Similar to the series of **units** `<OptionButton>` controls, add a series of **medication form** `<OptionButton>` controls that tracks the following medication forms:
  - **Tablet**
  - **Syrup**
  - **Patch**

## Merging State

Consider the following state object:

```
this.state = {
      title: "Merge Practice",
      shirtSizeOptions: ["xl", "l", "m", "s", "xs"],
      formState: {
        name: "",
        amount: 0,
        unit: "mg",
        description: ""
      }
    }
```

Notice the `formState` property value consists as an object within the parent `state` object.  To update the `amount` value within the `formState` object we will have to do a few steps:
  - Grab a copy of the `formState` object from the previous state.
  - Merge the `amount` value into the  `formState` object.
  - Merge the updated `formState` object into
  `state`.  

Below is an example of an event handler that uses a function to obtain the previous state and merge the new `name` value into the child `formState` object.  

Since Ramda's functions are immutable, `merge` merges the new `name` value into the `formState` object and returns a fresh copy of the `formState` object.  The copy is used to set the state.

 replacing formState with a function that provided previous state

```
handleNameChange(event) {
    const newValue = R.pathOr("whoops", ["target", "value"], event)

    this.setState(prevState => (
      {formState: R.merge(prevState.formState, {name: newValue})}
    ))
  }
```

- [Try it: Using Ramda's REPL to practice the `merge` function](https://goo.gl/1TEvRt)
- [Try it: React Forms Merging State with RamdaJS](http://codepen.io/tripott/pen/dWqRoe?editors=0011)

## Your turn: merging state

- Fork your previous codepen.
- In your constructor change the shape of your initial state object:
  - Add a property named `title` with a value of "Deep Merge"
  - Move the form state data into a property named `formState` as an object like this:

  ```
  this.state = {
      title: "Deep Merge"
      formState: {
        name: "",
        amount: 0,
        unit: "mg",
        description: ""
      }
    };
  ```
- Update the `<h2>` title of your form from "Controlled Component" to the `state.title` value
- Modify your inputs to retrieve the values from the new location in state.
- Modify your handleChange event handlers to merge the state into `formState`  

## Picking from a large number of options

Good User experience (UX) design states to display all selection options if under 6.  We utilize this design in our series of **units** `<OptionButton>` controls.  

> See [Design Better Forms](https://uxdesign.cc/design-better-forms-96fadca0f49c) for practical tips on good UX design.

But what if we have a large number of options to choose from?  What should we do?

Use a drop-down list to display a list of 6 to 25  options.

```
<div>
  <label className="db fw4 lh-copy f6">
    Select music genre
  </label>
  <select
    value={this.state.genre}
    onChange={this.handleGenreChange}
  >
    <option value="1">classic rock</option>
    <option value="2">alternative</option>
    <option value="3">country</option>
    <option value="4">hip hop</option>
    <option value="5">R and B</option>
    <option value="6">jazz</option>
  </select>
</div>
```

- [Try it: React Forms Create Drop Down List from Array](http://codepen.io/tripott/pen/KmxMJq?editors=0011)

## Your turn: Add a drop down list

- [Fork this codepen](http://codepen.io/tripott/pen/EmRMEd?editors=0011).
- Add a **Pick up location** drop down list to the form with the following options:
  - Downtown
  - Summerville
  - Moncks Corner
  - Goose Creek
  - Mount Pleasant
  - West Ashley
  - James Island
  - Daniel Island
  - Johns Island
  - Isle of Palms
- Refactor.  Instead of hard coding the values for the drop down list, dynamically supply the values from an array named `locations`.

## Submitting the form

- [Try Me: React Forms Simple Submit](http://codepen.io/tripott/pen/xdaLvG?editors=0010)
- [Try Me: React Forms Add with Fetch ](http://codepen.io/tripott/pen/dWqVvW?editors=0011)
- [Try Me: React Forms Handling Multiple Inputs ](http://codepen.io/tripott/pen/aWRBWO?editors=0011)

## Your Turn: Create a Person Add Form with fetch

- Fork this [React Add Patient Form Starter](http://codepen.io/tripott/pen/PmyxNy) codepen.
- Similar to the [medication add form](http://codepen.io/tripott/pen/aWRBWO?editors=0011), create patient add form.
- On submit, use Fetch to POST a new patient to your pharmacy api.
- Provide a status message for 200, 400, and 500 level HTTP status codes.
