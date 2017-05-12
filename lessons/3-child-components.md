# Lesson 3: Breaking a component into smaller pieces

## Student Prep

Review the following materials:

- https://facebook.github.io/react/docs/components-and-props.html#extracting-components

## Look for reuse opportunities

- Some components try to do too much.
- Hard to reason about.
- Hard to maintain.
- Look for ways to split the component up into reusable pieces.
- Having a palette of reusable components pays off in larger apps.
- A good rule of thumb is that if a part of your UI is used several times (Button, Panel, Avatar), or is complex enough on its own (App, FeedStory, Comment), it is a good candidate to be a reusable component.

## Try it and discuss

- Study the following [codepen](http://codepen.io/tripott/pen/XRqmdx).  
- How can we break it up into smaller, reusable, maintainable components?
- Demo breaking a component into smaller pieces.

## Your turn

- [Fork this pen](http://codepen.io/tripott/pen/OmZXzm?editors=0010) the pen to your account.  
- Break the single component into smaller components.
- Look for opportunities to pass props into each component, making it generic and reusable.
