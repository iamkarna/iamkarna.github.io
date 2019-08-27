---
theme: "night"
transition: "slide"
highlightTheme: "darkula"
---

# JS

---

## Object

collection of related data / functionalities (properties / methods)

---

```js
objTwo = {
    name:['yazhini','karunakaran'],
    age:20,
    greet: function(){
        console.log(this.name[1]+' '+this.name[0] + 'welcome');
    }
}
```
<small>* 'this' keyword refers current object

---

### access data

```js
// dot notation
objTwo.name
objTwo.name[1]
objTwo.greet()

// bracket notation
objTwo['name']
objTwo['name']['first']
```

---

#### pros <small>n</small> cons of dot / bracket 

- dot
    - easy to write
    
- bracket
    - set object member name and value dynamically 
    - set member name with space

---

### set data

```js
//update existing
objTwo.age = 30
objTwo['name']['first'] = 'thamizhini'

// new members
objTwo.hobby="Gardening"
objTwo.bye = function(){console.log('Bye!!')}
```
```js
// update / add dynamically
objTwo.name = myMemberValue
objTwo[myMemberName] = myMemberValue
```

---

### looks familier?

```js
//spilt method in String Class
myString.split(',')

//createElement method in document
var myDiv = document.createElement('div')
```

---

## oojs

#### oop

<!-- - instantiation <br><small>process of creating an object instance from class</small> -->

- encapsulation <br><small>data and functions stored and accessed through structure</small>
- abstraction <br><small>creating a simple model of more complex thing</small>
- inheritance <br><small>child classes have access to parent class</small>
- polymorphism <br><small>multiple object types to implement same functionality</small>

---

### constructor & instance

construtor is js version of class

```js
//constructor
function Person(name){
    this.name = name
    this.greeting = function(){console.log('hi')}
}
```

```js
//instance
var person1 = new Person('Bob');
var person2 = new Person('Sarah');
```

<small>* convention is that to write constructor function starts with capital letter</small>

---

### other way

```js
var person1 = new Object();

var person2 = Object.create(person1);
```

---

## prototype


---

# Fin
