# Forms

- Form elements keep internal state
- A 'normal' html / non-React form will browse to a new page when submitted.  This is typically not done with a React form.
- Use a JavaScript function to handle the submit including the data associated with the form.
- Use "controlled components" to track the data within each of the form elements as the user types in data.
- Data within the form elements are tracked in state.
- Form elements like `<input>` maintain their own state.
- State is updated as the user interacts with the form element.

[Try Me: React Forms Simple Controlled Component](http://codepen.io/tripott/pen/EmRMEd?editors=0011)
[Try Me: React Forms Add / Controlled Components ](http://codepen.io/tripott/pen/EmRMEd?editors=0010)
