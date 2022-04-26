---
title:  "[javascript] overview"
excerpt: "Describe how to use javascript"

categories:
  - web
tags:
  - [javscript]

toc: true
toc_sticky: true
 
date: 2022-04-22
last_modified_at: 2022-04-22
---

### var vs let

`var` is hoisted to the top of its scope

```javascript
    console.log(hi);
    var hi = "say hi";
```

`let` is limited to the block in which it is declared

### arrow function

```javascript
// Traditional Anonymous Function
function (a, b){
  return a + b + 100;
}

// Arrow Function
(a, b) => a + b + 100;

// Traditional Anonymous Function (no arguments)
let a = 4;
let b = 2;
function (){
  return a + b + 100;
}

// Arrow Function (no arguments)
let a = 4;
let b = 2;
() => a + b + 100;
```

### export/import

```javascript
// index.js
import React from "react";
import ReactDOM from "react-dom";
import Heading from "./Heading";

ReactDOM.render(
  <div>
    <Heading></Heading>
    <Heading />
    <ul>
      <li>Bacon</li>
      <li>Jamon</li>
      <li>Noodles</li>
    </ul>
  </div>,
  document.getElementById("root")
);

//  Heading.jsx
import React from "react";

function Heading() {
  return <h1>My Favourite Foods</h1>;
}

export default Heading;
```

### export vs export default

It's just convention. There's no diff between two.



### vscode extension
Babel JavaScript