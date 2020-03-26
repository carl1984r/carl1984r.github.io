---
layout: post
title:      "JavaScript:  Hoisting and Scoping"
date:       2020-03-25 04:04:23 -0400
permalink:  javascript_hoisting_and_scoping
---


Working on my JavaScript project has allowed for copious exposure to two significant aspects of the language:  Hoisting and Scoping.  Understanding scoping first definitely helped with understanding hoisting.    

Scope is the context in which things (values or expressions) can be accessed.  If a value or expression is not in the current scope - it will not be available for use.  A function for example creates a scope.  If a variable is created within a function - it cannot be accessed outside of the function or within other functions.  

Example:  
```
function newFunction() {
    var g = "example text";  // g can only be used in newFunction
    console.log("within function");
    console.log(g);
}
console.log(g);  // Produces error

```

VS

```
var g = "example text";  // g can be used within newFunction and outside newFunction
function newFunction() {    
    console.log("within function");
    console.log(g);
}
console.log(g);  // example text

```

Hoisting refers to how execution contexts work (creation and execution).  First, function and variable declarations are placed into memory (creation phase) - variable declarations will have default value of “undefined”.  During the execution phase, code execution proceeds line by line - real values are then assigned to variables already present in memory.  Since functions are loaded into memory during the creation phase, it will be available for use prior to function declaration (during execution - regardless of location in code).  

Example:
```
function addFirstName(name) {
  console.log("Your first name is " + name);
}

addFirstname("Steve");

/*
Output of the code is: "Your first name is Steve"
*/

```

The above works the same as:  

```
addFirstname("Steve");

function addFirstName(name) {
  console.log("Your first name is " + name);
}

/*
Output of the code is also: "Your first name is Steve"
*/

```

Declarations are hoisted.  Not initializations. If a variable (var) is declared and initialized after use, output will be undefined.

Example:  
```
console.log(name); // Output: undefined 
var name; // declaration
name = "Mike"; // initialization

```

While the var declarations are initialized with undefined, let and const declarations remain uninitialized until evaluation. Output results are relative to placement of let or const within code.

Example:
```
console.log(name); // Output: ReferenceError
let name; 
name = "David";

```

VS

```
let name; 
console.log(name); // Output: undefined
name = "David";

```


