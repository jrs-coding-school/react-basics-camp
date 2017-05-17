# Lesson 2: Props

## Student Prep

Review the following materials:

- https://facebook.github.io/react/docs/components-and-props.html

## Intro to Props

- A valid React component can be as simple as a JavaScript function that:
  - accepts a single "props" object argument with data
  - returns a React element.
- We call such components "functional" because they are literally JavaScript functions.

  [Try it](http://codepen.io/tripott/pen/zwRmMy)

## Creating lists, passing props down to children


### Keys
- When dealing with the display of lists, you'll want to provide React with a _stable_ way to identify each item in the list.  In this way React can efficiently manipulate the DOM to display the list again, should the data/state change.
- Keys used within arrays should be unique among their siblings.
- array indexes don't make for good id's as they can change if the data is reordered. Thereby making them unstable.
- Database primary key values do make for id's as they are stable.
- Keys serve as a hint to React but they don't get passed to your components. If you need the same value in your component, pass it explicitly as a prop with a different name

[Try it: simple list item and keys](http://codepen.io/tripott/pen/MmXzxX?editors=0011)

[Try it (Ramda Map)](http://codepen.io/tripott/pen/eWMVwj)

## Your turn: Make the children pretty

- Using the previous code pen as a template, [fork this pen](http://codepen.io/tripott/pen/eWMVwj) the pen to your account.  Reviewing the settings for the template you will see it contains a reference to react and react-dom libraries and tachyons css.
- Modify the code so that it looks like the image below:

  > Don't Panic!: See [tachyons.io](http://tachyons.io/components/) components.   [Peek](http://codepen.io/tripott/pen/xdWWpx?editors=0011) here if you need to look at the solution.

- The data for each child is located as an object within the `characters` array.
- Clicking the **More** button should navigate the browser to the url that provided by the `more` property.

![Make it look sooo shweeet](/img/makeitpretty.png)

## Conditional rendering

- Use conditional logic, such as an `if` statement or a ternary or a conditional operator such as `&&` to decide what to display in the UI based upon your state, such as the data within props.  

  [Try it](http://codepen.io/tripott/pen/MmXGGd?editors=0011)

```
const UserGreeting = props => {
  console.log("UserGreeting props", props)
  return (
    <div>
        <h1 className="pa3 fw3 f1 lh-title mt0 mb3 black">
          Welcome {R.propOr("", "userName", props.user)}
        </h1>
    </div>
  )
}


const SignUp = props => {
  console.log("SignUp props", props)
  return (
    <section className="ph3 ph5-ns pv5">
  <article className="mw8 center br2 ba b--light-blue bg-lightest-blue">
    <div className="dt-ns dt--fixed-ns w-100">
      <div className="pa3 pa4-ns dtc-ns v-mid">
        <div>
          <h2 className="fw4 blue mt0 mb3">This is a promo title </h2>
          <p className="black-70 measure lh-copy mv0">
            This is suporting copy for the wonderful promo catchphrase that is going to be used.
          </p>
        </div>
      </div>
      <div className="pa3 pa4-ns dtc-ns v-mid">
        <a href="#" className="no-underline f6 tc db w-100 pv3 bg-animate bg-blue hover-bg-dark-blue white br2">Sign up for free</a>
      </div>
    </div>
  </article>
</section>
  )
}

const Header = props => {
 return R.prop("isAuthenticated", props.user) === true  ?  <UserGreeting {...props} /> : <SignUp {...props}/>

};


// simulate a user object and pass as props to the Header component.  
//  Don't worry, Header knows what to do based on the state.
const user = {isAuthenticated: true,  userName: "Jeff"}
// const user = {isAuthenticated: false}


ReactDOM.render(<Header user={user} />, document.getElementById("root"));
```

## Element Variables

- You can use variables to store elements.
- For example, you can conditionally render elements inline using the JavaScript conditional operator

[Try it](http://codepen.io/tripott/pen/PmaBaz?editors=0010)


```
const SignUpButton = props => {
  return (
    <div className="pa3 pa4-ns dtc-ns v-mid">
      <a
        href="#"
        className="no-underline f6 tc db w-100 pv3 bg-animate bg-blue hover-bg-dark-blue white br2"
      >
        Sign up for free
      </a>
    </div>
  );
};

const ProfileButton = props => {
  return (
    <div className="pa3 pa4-ns dtc-ns v-mid">
      <a
        href="#"
        className="no-underline f6 tc db w-100 pv3 bg-animate bg-black hover-bg-dark-blue white br2"
      >
        My Account
      </a>
    </div>
  );
};

const Header = props => {

  const HeaderButton = R.prop("isAuthenticated", props.user) === true
    ? <ProfileButton {...props} />
    : <SignUpButton {...props} />

  return HeaderButton
};

// simulate a user object and pass as props to the Header component.
//  Don't worry, Header knows what to do based on the state.
const user = { isAuthenticated: true, userName: "Jeff" };
// const user = {isAuthenticated: false}

ReactDOM.render(<Header user={user} />, document.getElementById("root"));
```
