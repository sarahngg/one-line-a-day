# one-line-a-day

***


## May 16, 2019 | Thur

JavaScript tutorials

### Main technologies:

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
- anonymous functions

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

***


## May 15, 2019 | Wed

Created, committed, pushed repositories from command line.

### Main technologies: 

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

***


## May 14, 2019 | Tue

### Main technologies

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

***


## May 13, 2019 | Mon

### Main technologies

C++ and memory

- We can directly manipulate memory in C++
- Each memory cell has an address, data

***


## May 12, 2019 | Sun

### Main technologies

- HTML
- CSS
- JavaScript

### Activity summary

Created a message board website

- Set up style sheet and html file
- Used JS to clear text box and add textbox entry to a list and display it
- Learned about `parse` and `stringify` JSON 

***


## May 11, 2019 | Sat

### Main technologies

- HTML
- CSS
- JavaScript

### Activity summary

- Reviewed HTML and CSS
- Started JavaScript tutorials