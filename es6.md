---
theme: "night"
customTheme : "me"
transition: "slide"
highlightTheme: "darkula"
title: "es6"
---

# es6

Understanding es6

>nicholas c. zakas

---

## block bindings

---

### `var` declarations & hoisting

```js
function getValue(condition) {
    if (condition) {
        var value = "blue";
        // other code
        return value;
    } else {
        // value exists here with a value of undefined
        return null;
    }
// value exists here with a value of undefined
}
```

--

```js
//The declaration of value is hoisted to the top
function getValue(condition) {
    var value;
    if (condition) {
        value = "blue";
        // other code
        return value;
    } else {
        return null;
    }
}
```

---

### block-level declarations

inaccessible outside a given block scope and also called lexical scopes.

- Inside a function or a block

---

#### `let` declarations

`var` can be replaced with `let` to declare a variable but limited to the current code block scope and not hoisted to the top of the enclosing block

```js
function getValue(condition) {
    if (condition) {
        let value = "blue";
        // other code
        return value;
    } else {
        // value doesn't exist here
        return null;
    }
    // value doesn't exist here
}
```

--

#### no redeclaration

```js
var count = 30;
// throws an error
let count = 40;
```

-

```js
var count = 30;
if (condition) {
    // doesn't throw an error
    let count = 40;
    // more code
}
```

