# one-line-a-day

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
