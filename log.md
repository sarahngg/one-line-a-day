## July 5, 2019 | Fri

### Take-home Assignment Project Summary

#### Project Requirements

- It must look and feel good across **all** screen sizes
- Create a `README.md` file with simple instructions to run the app.
- Create a search page with a search bar. Users should be able to paste a GitHub repo URL here.
- Create a results page that displays **all** (open, closed, pull requests) issues from the search query.
- Indicate which issues are closed or pull requests using the icons.
- Implement filtering by open, closed, or pull requests on the results page.

#### Bonus Features Attempted

- Add indicators for search progress.
- Cover the case of an error fetching the results.
- Implement pagination with multiple pages

#### Future Improvement

* Pagination: No limit on page increment even though there may not be a next page
* Limit issue title and body length
* Learn more about GItHub API, provide a schema for GitHub API to only return data that I need
* Learn more about frontend testing methods

#### Challenges

* Creating my second major JavaScript project
* Deciding React folder structure
* Understanding the non-exclusive nature of issues and pull requests
* Deciding what should be a component and what should not
* Understanding CSS grid and flexbox
* Deciding what to put in store vs. component state
* GET-ting data from GitHub API with pagination
* Deciding whether or not to store all issues and filter them or GET with queries when selected filter changed

#### Outsourced

* parse-github-url: Parsing GitHub repo url for user and repo name
* Axios: Fetching data from GitHub API
* Responsiveness: CSS Grid
* CSS loading indicator

## June 31, 2019 | Sun

CSS

* flex <https://css-tricks.com/snippets/css/a-guide-to-flexbox/>
* box shadow <https://www.w3schools.com/css/css3_shadows.asp>

To-do

coloring svg to right color
https://facebook.github.io/create-react-app/docs/adding-images-fonts-and-files#adding-svgs
https://stackoverflow.com/questions/42296499/how-to-display-svg-icons-svg-files-in-ui-using-react-component

make input placeholder text scale with screen width

## June 29, 2019 | Sat

create-react-app

* installed successfully using a different router

CSS

* used @font-face
  * @**font**-**face** is a css rule which allows you to download a particular **font** from your server to render a webpage if the user hasn't got that **font** installed. This means that web designers will no longer have to adhere to a particular set of "web safe" **fonts** that the user has pre-installed on their computer.
* <https://css-tricks.com/whats-deal-declaring-font-properties-font-face/>

## June 28, 2019 | Fri

CPSC 221 Final Exam

* Done!

React app

* Failed to create-react-app

## June 24, 2019 | Mon

Git - Revert a pushed commit

<https://gist.github.com/gunjanpatel/18f9e4d1eb609597c50c2118e416e6a6>

GitHub Issue List API

<https://api.github.com/repos/sarahngg/chat-with-gossip-girl/issues?state=all>

## June 19, 2019 | Wed

`chat-with-gossipgirl` Personal Project Demo

### Server

* Stored the initial set of messages in a JavaScript array in `api/routes/messages.js`
  * Set up Express router for GET, POST, and DELETE (additional) requests
  * Note: DELETE request only deletes the newest message using `pop()`

* Used Postman to verify the requests works
* Handled asynchronous calls in  `src/actions/index.js`
  * `redux-thunk` in `api/app.js`

### Extra

* Moved actions from component to `src/actions/index.js`
* Declared action types as constants for single point of control
* Added contact bar on top with name, details, and back
* Improved speech bubble colors to match the iMessage colors
* Hover to show message id

### Challenges

* How to handle the duplication of data in redux and server?
* Where should the business logic go? Currently in `rootReducer`
* How to split the reducers?
* How to keep a count of messages

## June 16, 2019 | Sun

<https://redux.js.org/advanced/async-actions>

Asynchronous API has two crucial moments in time

* the moment you start the call
* the moment when you receive an answer (or a timeout)

These moments require a change in state, so we need to dispatch normal actions that will be processed by reducers synchronously.

For any API request, we dispatch these actions informing the reducers that:

* The request began
  * eg. toggle `isFetching` flag in state to show spinner in UI
* The request finished successfully
  * eg. merging new data into the state and resetting `isFetching` so UI hide spinner and display fetched data
* The request failed
  * eg. resetting `isFetching` and store the error message to display in UI

## June 15, 2019 | Sat

NodeJS

JavaScript Engines

* Converts JavaScript to machine code

* Node.js is written in C++
* Eg. V8 - created by Google

```javascript
/*
  The Global Object
  https://nodejs.org/api/globals.html
*/
setTimeout(function(){
  console.log('3 seconds have passed');
}, 3000);

var time = 0;
var timer = setInterval(function(){
  time +=2;
  console.log(time + ' seconds have passed');
  if (time > 5) {
    clearInterval(timer);
  }
}, 2000);

// Prints directory
console.log(__dirname);

// Prints file
console.log(__filename);

/* 
  Function Expressions
  - common expression in node
*/

// Normal function statement
function sayHi(){
  console.log('hi');
}

sayHi(); // invoke function by name

// Function expression - anoymous function
var sayBye = function(){ // set anon function to variable
  console.log('bye');
};

//sayBye(); // invoke function by var()

function callFunction(fun) {
  console.log('This function takes another function as a param');
  fun(); // then call the function
}

callFunction(sayBye);
```

### Modules and Require

In app.js

```javascript
// require the counter module returns whatever is in module.exports in count.js
var counter = require('./counter');


console.log(counter(["this", "that", "those"]));
```

In count.js

```javascript
var counter = function(arr) {
  return "There are " + arr.length + " elements in this array"
};
//explicitly say what part of the module we want to make available to file that `requre` this module
module.exports = counter;
```

### Module Patterns

There are several ways to export multiple things in the export object 

In app.js

```javascript
var stuff = require('./stuff');

console.log(stuff.counter(["this", "that", "those"]));
console.log(stuff.adder(5,6));
console.log(stuff.adder(5,stuff.pi));
```

In stuff.js

```javascript
var counter = function(arr) {
  return "There are " + arr.length + " elements in this array"
};

var adder = function(a,b){
    return `The sum of the 2 numbers is ${a+b}`;
};

var pi = 3.142;

// Add properties to the export object
// Original: module.exports = counter;
module.exports.counter = counter;
module.exports.adder = adder;
module.exports.pi = pi;
```

```javascript
module.exports.counter = function(arr) {
  return "There are " + arr.length + " elements in this array"
};

module.exports.adder = function(a,b){
    return `The sum of the 2 numbers is ${a+b}`;
};

module.exports.pi = 3.142;
```

```javascript
var counter = function(arr) {
  return "There are " + arr.length + " elements in this array"
};

var adder = function(a,b){
    return `The sum of the 2 numbers is ${a+b}`;
};

var pi = 3.142;

module.exports = {
    counter: counter,
    adder: adder,
    pi: pi
};
```

## May 31, 2019 | Fri

React, Redux Tutorial - switched to video format

### Set up index.html

* add an HTML element - this will be where react renders your component
* Note: may need to go to `/public` to find the `index.html` if using boilerplate project from react

```html
<div id="an-html-element"></div>
```

### JS

```jsx
class AnAwesomeComponent extends React.Component {
	//must have at least the render method
	render() {
		//JSX template goes in return
		return(
			<div classname="a-css-class"></div>
		)
	}
}
```

### JSX

* write HTML code within a JavaScript block
* Limitations
  1. Can only return one root element - wrap in a div if more than one
  2. `class` cannot be used to add a CSS class to an element - use `className` instead

### Render

To tell react to render the component, pass in 

* the component name `<AnAwesomeComponent />`
* where to render it `document.getElementById('an-html-element')`

```javascript
ReactDOM.render(
	<AnAwesomeComponent />,document.getElementById('an-html-element')
);
```

### Dynamic JavaScript rendering

We want to use JS within the HTML elements returned in render, because displaying static things are not that interesting.

Wrap dynamic content in `{}` like `{Math.floor(Math.random() * 10)}` in the return value

```jsx
class App extends React.Component {
    render(){
        
        return (
            <div>
                <h1>Hello werld</h1>
                <p>{Math.floor(Math.random() * 10)}</p>
            </div>
        );
    }
}
```

### Component State

State of UI and data

Example:

```jsx
{
	showPopup: true
}
```

Ways to define state

Inside the component

```jsx
state = { 
    someStateName: on, 
    anotherStateName: 6,
    moreStateName: "oh no"
}
```

Rendering the state in JSX in the same component

```jsx
render(){
    return (
        <div>
        	<h1>Message List</h1>
        	<p>{this.state.moreStateName}: {this.state.anotherStateName}</p>
		</div>
	);
}
```

### Event

Attaching an event handler to an element

`onClick = {this.aFunctionToHandleAnEvent}`

* `on` EventName
  * onClick
  * onCopy
  * onMouseOver
* define `aFunctionToHandleAnEvent` in the component
* `{this.aFunctionToHandleAnEvent}`function wrapped in `{}` because we are rendering dynamic info/JS
* `this` refers to the component where the function is defined
* no `()` after `this.aFunctionToHandleAnEvent` because we do not want to invoke the function right away when the page loads - only want to invoke when event happens

`aFunctionToHandleAnEvent(e)`

* `e` is the event object - contains many other properties in the event (eg. pageX pageY - xy coordinate of mouse on screen of the event)

```jsx
aFunctionToHandleAnEvent(e){
        console.log(e.target)
    }
render(){
    return (
        <div>
            <button onClick={this.aFunctionToHandleAnEvent}>Click</button>
        </div>
    );
}
```

### Using arrow functions to bind `this` and access component state

In a DOM event, the `this` context is lost/scope is different when the event handling function is called. So this will not work:

```javascript
aFunctionToHandleAnEvent(e){
        console.log(this.state) //this = undefined
    }
```

Arrow functions bind the context of `this` to the component instance

```javascript
aFunctionToHandleAnEvent = (e) => {
        console.log(this.state)
    }
```

### Using `this.setState` to change state in a function

Update state using `setState()`  and list the state properties you want to change. React will only change those and keep other properties intact.

```javascript
aFunctionToHandleAnEvent = (e) => {
        // instead of
    	// this.state.name = "new name";
    	// do
    	this.setState({
            name: "new name",
            age: 20
        })
    }
```

### Working with forms

```jsx
<form onSubmit = {this.handleSubmit}>
    <input type="text" onChange={this.handleFormChange}/>
    <button>Submit</button>
</form>
```

Event handling functions

```javascript
handleFormChange =(e)=> {
    this.setState({
        message: e.target.value
    });
}

handleSubmit =(e)=> {
    //prevent default behaviour: refreshing page after submit
    e.preventDefault(); 
    console.log("Form submitted!", this.state.message);
}
```

### Create React App

* command line tool to make react apps
* keep code modular
* use ES6 features

`npx create-react-app appname`

Using terminal in VS Code ``Ctrl+` ``

Folder structure

* node_modules - 3rd party dependancies
* public - serve to browser
* src - our work

### Single Page App

* Only request page from server once - request the index.html file
* React handles the subsequent request and give faster response to the app

Root component

* mother of all components
* other components are nested in it

### Nesting a component within another

Make code more modular

In the child:

```jsx
import React, { Component } from 'react';

class ChildComponent extends Component {
    render() {
        ...
        )
    }
}

export default ChildComponent;
```

In the parent:

```jsx
import React, { Component } from 'react';
import ChildComponent from './ChildComponent';

class Parent extends Component {
    render() {
        return (
            <div className="Parent">
                <ChildComponent />
            </div>
        )
    }
}

//if nested in another component
export default Parent;
```

### Passing data from parent to child component via `props`

In the child:

```jsx
class ChildComponent extends Component {
    render() {
        //Destructuring: storing props in variable
        const {name, age} = this.props;
        return (
            <div className="child">
                <div>Name: {name}</div>
                <div>Age: {age}</div>
            </div> 
        )
}
```

In the parent:

```jsx
class Parent extends Component {
    render() {
        return (
            <div className="parent">
                <ChildComponent name="Child A" age="5"/>
                <ChildComponent name="Child B" age="3"/>
            </div>
        )
    }
}
```

## May 30, 2019 | Thur

### C++ associative array

* `auto` type inference
* `auto lookup = map.find(key)` returns an iterator to an element with key equivalent to `key` 
  * if not found, `lookup` is `map.end()`
  * if found, dereferencing the iterator `lookup` will give a `std::pair`
* `pair.first` is the key and `pair.second` is the value

### React Tutorial

#### JSX

- can put any JavaScript expressions within braces inside JSX
- Event handlers
  - onClick
  - onMouseOver

#### Arrow Function Syntax

`onClick={() => alert('click')}` instead of `onClick={function() { alert('click'); }`

#### State

* React component use `state` to remember things
  * setting `this.state` in constructors - should be private



Note: All React component classes that have a `constructor` should start it with a `super(props)` call.

Question:

- When does a React component need/not need a constructor?



## May 29, 2019 | Wed

### React, Redux, JS

[Tutorial](https://reactjs.org/tutorial/tutorial.html#before-we-start-the-tutorial)

* [Arrow Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) - like a function but without its own **bindings** - cannot be used as constructors

### React

* efficient and flexible JS library for building UI
* breakdown complex UI into components

#### `props`

* properties
* `React.Component` subclass takes parameters called `props` - properties and returns a hierachy of views to display via `render()`

#### `render()`

* returns a **React element** - what to render
* react takes this info and display on screen

## May 25, 2019 | Sat

### Scrum Update

What did you work on this past iteration (2 weeks)?

* Sketched prototypes for menu page, journal page
* Pitched idea to team

What were any major issues/challenges you ran into?

- Proposing features that I am not sure how to implement
  - Searching keyword
  - Storing many types of data and retrieving them

What do you plan to work on for this coming iteration (2 weeks)?

* Do react and redux tutorial on freecodecamp and lynda
* Prototype UI - Material UI
  * Finalize drawer
* Make glossary (give names to things)



## May 23, 2019 | Thur

### Project

* Set up sarahngg.github.io
* Played around with colours and styling in CSS
* Installed Meteor and React

## May 22, 2019 | Wed

### Project Review

<https://github.com/sarahngg/message-board>

### Difficulties

- Visualizing how elements will render on screen simply by looking at the code
- Constant iteration of css styles 
- Understanding JSON string and JSON object
- Deciding between css class or id when applying styles
- Understanding specification (sometimes ambiguous like the clear function)

### Additional Functionality

* Google Font
* Emoji support
* Random emoji when no name is entered
* Name field in form
* Clearing text area text after form submission
* Resizing when screen size changes

### What I learned

- Steal color theme/palette from websites I like by inspecting elements
- Visualize webpage as many div boxes within many div boxes rather than thinking element-wise
- freecodecamp javascript tutorial

## May 21, 2019 | Tue
### Technologies:

C++

#### Destructor

* Gives back resources to the system
* Called implicitly when
  1. The object goes out of scope
  2. `delete` is called on a pointer
* No parameters/return type (can’t be overloaded)
* Specific name: `~ClassName()`

##### Default Destructor

* Supplied by compiler
* Empty and does nothing

##### Expected Functionality

When an object goes out of scope/`delete` is called on a pointer

1. The object destructor is called `~Object()`
   * Specific request for outside resources is freed

2. Destructors of the member variables are called one by one
   * Primitive types (including pointer) - do nothing
     * Pointer destructor does not deallocate memory → memory leak
     * Therefore must call `delete` on pointer to free dynamic memory
   * Non-primitive types - their destructors are called and we trust them to clean up



## May 20, 2019 | Mon

### Technologies:

C++

#### Copy Constructor

- A constructor that takes a parameter of an object of the same class, eg. `Object (const Object& originalObject);`
- Used for initializing a copy of `originalObject`
- Private members can be accessed - copy constructor and `originalObject` belong to the same class

##### Default Copy Constructor

- Compiler always supply a copy constructor
- Primitive types including pointers are copied bitwise 
  - Pointer is copied with the same memory address as the old object pointer without dereferencing, rather than having its own copy of the dynamic memory
- Only soft copy will be made (top level)

##### Writing a Copy Constructor for Member Pointers

* Hard copy with be made such that the original object and the copied object are independent in memory usage
* Generally needed when the class have pointers as member data

`copiedPointer = new Object(originalObject->data);`

## May 17, 2019 | Fri

### Technologies:

C++

#### Constructors

* Default constructor
  * initialize object to default state
  * initialize variables (“clearing” garbage value)
    * usually set integers to `0` and pointers to `NULL`
  * given by the compiler unless we write **any** constructor (default or not)
  * used in declaring arrays of objects `Object myArray[3]`

* `new Object();` - dynamic
  1. Set aside memory for the object
  2. Then call the constructor to initialize that memory
  3. Finally returns the address of the dynamic object
* `Object o1;` - local
  * NOTE: Do not use `()` for default constructor to indicate it is not a function declaration
    * Variable declaration:  `Object o;`
    * Function declaration: `Coord c4();`

## May 16, 2019 | Thur

### Technologies:

- JavaScript
- C++

#### JavaScript variables

- `let` vs `var ` variables
  - `var` allow duplicate variable declarations with no error but `let` will throw error
  - global scope of `var` can go out of control but `let` limits scope within the block, statement, or expression it is declared
- `const` variables
  - like `let` but read only
  - a `const` array’s content can be mutated by assigning values individually to the array cells, but the array reference variable is non-mutable
    - Use `Object.freeze(obj)` to prevent object mutation
- Anonymous functions

```
// const magic = function() {
//   return new Date();
// };

const magic = () => new Date();
```

- `"use strict";`
  - Strict mode does not allow the use of undeclared variables

#### C++ Arrays and Strings

- Local array declaration (no `new` is needed)

  ```int x[6];``` 

- Arrays can be created locally (in stack) and dynamically (in heap)

- Memory address allocated for array cells are consecutive, where the size depends on the type stored

- Each cell in the array are not individually named but can be referred by `x[0]`, `x[2]` and so on

- The array name `x` is a stand-in for the start address of the array, but is not an *lvalue* (`x` cannot be written to but `x[2]` can be)

- The compiler can calculate the address of a specific cell in an array given 

  1. the starting address of the array
  2. the index of the specific cell
  3. \# bytes needed to store the type of data in each cell

- pointer + integer = address



## May 15, 2019 | Wed

Created, committed, pushed repositories from command line.

### Technologies: 

Git

- Some useful git commands:
  - `git add .` adds files to staging area
  - `git status` lists new/modified files to be commited
  - `git clone` downloads a project and its version history
  - `git commit` commits changes in local machine
  - `git commit -m “message”` or `git commit` then get prompted to add long form messages
  - `git push` uploads local branch commits

### Random things learned

- `ls` command only works on Mac and Linux, use `dir` in Windows



## May 14, 2019 | Tue

### Technologies

C++ Pointers

- `int* numPtr` reads a type integer pointer named numPtr
- a pointer holds the memory address of the object it refers to
- `(object).(member function)` is equivalent to `(pointer to object)->(member function)`

`&` operator 

- address of the variable it appears before (in an executable line of code)

  `numPtr = &x` assigns the address of x to numPtr

- pass by reference when appearing in front of a variable in a function parameter

`*` operator

- dereferencing a pointer

  `*numPtr` returns the object held by numPtr

- declaring a pointer

  `int* numPtr`



## May 13, 2019 | Mon

### Technologies

C++ and memory

- We can directly manipulate memory in C++
- Each memory cell has an address, data



## May 12, 2019 | Sun

### Technologies

- HTML
- CSS
- JavaScript

### Activity summary

Created a message board website

- Set up style sheet and html file
- Used JS to clear text box and add textbox entry to a list and display it
- Learned about `parse` and `stringify` JSON 



## May 11, 2019 | Sat

### Technologies

- HTML
- CSS
- JavaScript

### Activity summary

- Reviewed HTML and CSS
- Started JavaScript tutorials
