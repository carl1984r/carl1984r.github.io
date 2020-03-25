---
layout: post
title:      "JavaScript:  Hoisting and Scoping"
date:       2020-03-25 08:04:22 +0000
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

Hoisting refers to how execution contexts work (creation and execution).  First, function and variable declarations are placed into memory (creation phase) - variable declarations will have default value of “undefined”.  During the execution phase, code execution proceeds line by line - real values are then assigned to variables already present in memory.  Since functions are loaded into memory during the creation phase, it will be available for use prior to function declaration (during execution - regardless of placement in code).  
