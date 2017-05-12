# Lesson 2: Props

## Student Prep

Review the following materials:

- https://facebook.github.io/react/docs/components-and-props.html

## Intro to Props

- A valid React component can be as simple as a JavaScript function that:
  - accepts a single "props" object argument with data
  - returns a React element.
- We call such components "functional" because they are literally JavaScript functions.

## Try it

- [React Simple Stateless Functional Component - Props](http://codepen.io/tripott/pen/zwRmMy)
- [React Stateless Functional Component - Passing Props Down to Children](http://codepen.io/tripott/pen/eWMVwj)

## Your turn: Make the children pretty

- Using the previous code pen as a template, [fork this pen](http://codepen.io/tripott/pen/eWMVwj) the pen to your account.  Reviewing the settings for the template you will see it contains a reference to react and react-dom libraries and tachyons css.
- Modify the code so that it looks like the image below:

  > Don't Panic!: See [tachyons.io](http://tachyons.io/components/) components.

- The data for each child is located as an object within the `characters` array.
- Clicking the **More** button should navigate the browser to the url that provided by the `more` property.

![Make it look sooo shweeet](/img/makeitpretty.png)
