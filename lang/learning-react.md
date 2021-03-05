
# About

* [Learning React: Functional Web Development with React and Redux](http://shop.oreilly.com/product/0636920049579.do)
* by Alex Banks, Eve Porcello
* published by O'Reilly, 2017

# Thoughts

Nice intro to ECMA6, reasonably concise read.

# Take-Aways

* Functional Guidelines: use immutable data, use pure functions, favour recursion over looping
* var, const, let - conditional blocks do not create a new scope with var, fix with let
* arrow functions protect the value of this, function keyword blocks off the scope of this
* using import instead of script tag helps webpack to properly include dependencies

# Concepts

* `...` - Spread Operator
* `import` vs `require` - imports use ES6 modules
* `Object.assign` - copies enumerable and own props, shallow clone, merge objects
* `Object.keys`
* `React.createClass` - in the first version of React (2013) this was the only way to define a new React component, however it is now a candidate to be deprecated
* `React.createElement(tag, props, content)` - creates and returns a React element; can take any number of children as args, resulting React element has a props.children array as a member; eg. `React.createElement("h1", {id:"myHeader"}, "Hello")` becomes `<h1 id="myHeader">Hello</h1>`
* `React.createFactory` - define a React component from an object, alternative to createClass
* `ReactDOM.render` / `renderToString` / `renderToStaticMarkup` - server-side methods that render React components
* Array - JS lists; `Array.concat` leaves the original array unchanged, `Array.push` does not; Array.map, Array.reduce, Array.join, Array.filter, Array.reduceRight
* Babel Presets - option that specifies what transformation set to use
* className - "class" is a JavaScript reserved word, React uses className in props
* CommonJS - project to define a standard JS environment outside of the web browser context
* data-reactroot - an attribute on the root element of a React component
* Destructuring Assignment - syntax for locally scoping selective fields of an object, eg. `var { bread, meat } = sandwich;` where sandwich object has bread, meat, and other props
* DOM API - [Mozilla docs](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model); updating the DOM is relatively fast, inserting elements is relatively slow
* ECMA - European Computer Manufacturers Association
* Factories - built-in React.DOM.div factory, other html tags too; beware, considered harmful
* Feature Flagging - a good web build tool will allow this as a build-time config
* HMR - Hot Module Replacement, JS file hot-swapping for dev
* JSX - JavaScript as XML; uses `{}` to contain expressions; can be embedded in JS
* Modules - export const, export default
* Object Literal Enhancement - opposite of destructuring, turns scoped vars into an object
* Predicate - a function that always returns a bool
* Promises
* React - version 0.14 split into React and ReactDOM, eventually React Native was added; minimum reqs for pure react: react.js, react-dom.js, container div (id="react-container")
* Source Map - maps js build to source files for debugging; webpack config should include `devtool: '#source-map'`
* SPA - Single Page Application, updates the DOM instead of loading new pages
* Stateless Components - consider MVC architecture; components ideally are passed everything that they need to render (as React props)
* Template Strings - using `${}` syntax
* this.props - used to access props object (passed to ReactDOM.render call) from class member functions
* Virtual DOM - provided by React, changes are applied here first; browser DOM is comprised of DOM elements; virtual DOM is comprised of React elements
* Webpack Loader - what webpack calls plug-ins

# Techs

* Babel - JS transpiler, convert ES6+ into ES5; originally called 6to5, renamed in Feb 2015; including babel-core.js will transpile any `<script type="text/babel">` blocks, Babel v5.8 only; prod apps should transpile at build time
* Browserify - web build tool
* CodeBin - online JS tool
* ECMAScript - JavaScript's proper name; new versions of the standard are named by year starting with ECMAScript2015
* Ember CLI - tools for generating Ember.js web apps, influenced create-react-app
* Fiber - a new React core that improves rendering speed
* Grunt - web build tool
* Gulp - web build tool
* JSBin - online JS tool
* JSFiddle - online JS tool
* React Developer Tools - browser extension
* react-detector - Chrome extension
* show-me-the-react - Chrome extension
* Webpack - used to build web apps, can be used for build-time transpilation
* Yarn - package manager purported to be faster than npm

# Publications

* [Create Apps with No Configuration](https://reactjs.org/blog/2016/07/22/create-apps-with-no-configuration.html)
* [Lambda Calculus Then and Now (pdf)](https://turing100.acm.org/lambda_calculus_timeline.pdf)
* http://eloquentjavascript.net/
* http://functionaljs.com/

# Code

* `<MyComponent {...myObject}>` // common pattern for populating a JSX component's props from a JS object using the spread operator
* `var [last] = [...myList].reverse();` // grab last element with a copy, does not touch myList
* `const [first, ...rest] = myList;` // decompose myList into first, rest
* `function myFunc(...args)` // operates on arguments as an array
* `import * as myLib from './myLib.js'`
* ` const createScream = logger => message => logger(message.toUpperCase() + "!!!")`
* `(color, rating) => { return Object.assign({}, color, { rating: rating }); }` // set rating on clone
* `(color, rating) => ({ ...color, rating });` // same as above but using spread operator
* `const max = (arr) => { arr.reduce((max, value) => { return (value ? max) ? value : max; }, Number.MIN_VALUE); }`
* `const arrayToDict = (arr) => { arr.reduce((dict, obj) => { dict[obj.id] = obj; return dict; }, {}); }`
* `const uniq = (arr) => { arr.reduce((newArr, value) => (newArr.indexOf(value) !== -1 ? newArr : [...newArr, value], []); }`
* `id = { name.toLowerCase().replace ( / /g , "-" )}` // hacky way to convert object.name to a valid JSX property name

Currying Example

```
const userLogs = user => message => console.log(`${user.name}: ${message}`);
const log = userLogs(myUser);
```

Compose Example

```
// return a function that composes any number of input functions
// (use reduceRight instead to compose in reverse order)
const compose = (...fns) =>  // turns args into array
    (arg) => fns.reduce( (composed, f) => f(composed), arg);
```
