
# Setup

Building a React.js App with `create-react-app`

## Student Prep

Review the following materials:

- https://nodesource.com/blog/an-absolute-beginners-guide-to-using-npm
- https://yarnpkg.com/en/docs/getting-started
- https://github.com/facebookincubator/create-react-app#getting-started
- [Babel and JavaScript ES6 features](http://babeljs.io/learn-es2015/)

## Install Dependencies

### Yarn

- See https://yarnpkg.com/en/docs/getting-started and complete installation instructions https://yarnpkg.com/en/docs/install.

### NPM version 6

You will need Node >= version 6.  The Node installation is only required for Create React App itself.  https://nodejs.org/en/

Run the following command to check your node installation:

```
$ node -v
```

## Preparing a new project with `create-react-app`

With `create-react-app`, you don’t need to install or configure tools like Webpack or Babel.  They are preconfigured and hidden so that you can focus on the code.  Babel allows us to write JSX, JavaScript in ES6 syntax.  Babel will compile our code into a format that the web browser can read.  ES6 allows you to use arrow functions, classes, template literals, `let`, and `const` statements. You can use [Babel REPL](http://babeljs.io/repl/#?babili=false&evaluate=true&lineWrap=false&presets=es2015%2Creact&experimental=false&loose=false&spec=false&code=const%20element%20%3D%20%3Ch1%3EHello%2C%20world!%3C%2Fh1%3E%3B%0Aconst%20container%20%3D%20document.getElementById('root')%3B%0AReactDOM.render(element%2C%20container)%3B%0A) to check what ES6 code compiles to.

Once you have installed `create-react-app` globally, you can use it to bootstrap (create) a new react project.

- Install `create-react-app` globally (one time thing)
- Change to your "code" directory.
- Create a new react app with `create-react-app`.  This will configure Webpack and Babel.  It will also install two key dependencies - libraries - modules: `react` and  `react-dom`.
- Inspect the contents of **node_modules** folder.  Note the `react` and  `react-dom` libraries along with Babel and webpack.

  ```
  $ npm install -g create-react-app
  $ cd {your **code** directory}
  $ create-react-app pharma-student-react
  $ cd pharma-student-react
  $ ls
  $ cd node_modules
  $ ls
  $ cd ..
  ```

## Inspecting the project

Lets take a tour at the files and folders created when you called `create-react-app`.

- Open **public/index.html**.  The `div` tag with an `id="root"` is the mounting point for our react application:

```
<body>
<div id="root"></div>
<!--
This HTML file is a template.
If you open it directly in the browser, you will see an empty page.

You can add webfonts, meta tags, or analytics to this file.
The build step will place the bundled scripts into the <body> tag.

To begin the development, run `npm start`.
To create a production bundle, use `npm run build`.
-->
</body>
```

- When we build our application a `script` tag will contain `src` attribute that points to a bundle containing our React code.  So all our code, components, and JSX will be _transpiled_ from ECMAScript 2015 / ES 2015 / ES6 (all names for the same thing) into "normal" JavaScript.  Webpack and Babel are the tools used by react to transpile your code.

Example:

```
...
  <script type="text/javascript"
    src="/static/js/main.0e9ef5ab.js"></script>
  </body>
</html>
```

- Open **src/index.js**.  This React component is our entry point into our React application. Webpack will take the code within this file and build a bundle file by running the code through a series of transformations (transpilations).

- Since **index.js** is a component, you must import the `React` library. Also, since we are rendering our react application client side, within a web browser, we have to import `ReactDOM`.  We also import the `App` component that resides within the **App.js** file.

- Remember `<div id="root"></div>` tag within **index.html**?  At the bottom of **index.js** you will see we are rending the App component within **index.html** `root` element.

## Test our React App

- Run `npm start` from the terminal.  The app should open within a new tab at http://localhost:3000/.
