# JavaScript Notes

- **Notes from 'Getting started with JavaScript' course by @getify at [Frontend Masters](https://frontendmasters.com/courses/getting-started-javascript-v2/)**
- [You Don't Know JS book](https://github.com/getify/You-Dont-Know-JS)

## Values

- 42 -> Number
- 3.14 -> Number

- "Hello, friend" -> String

- true -> Boolean
- false -> Boolean

- null -> Empty value
- undefined -> Empty value

- [1, 2, 3]   -> Collection of values (Array)
- {name: "Kyle"}  -> Collection of values - Object (key:value)

## Operations

- 3 + 4     -> Arithmetic - Binary operator
- 43 - 1    -> Arithmetic - Binary operator

- "Kyle " + "Simpson"

- !false    -> Unary operator - Boolean

- 3.0 == 3  -> Comparison   | === (checks even if datatypes' are the same)

- 3 < 4

- true || false     -> Boolean operator: || (OR); && (AND)

## Types

- typeof 42 // "number"    (unary operator)
- typeof "Kyle" // "string"
- typeof true // "boolean"
- typeof undefined // "undefined"
- typeof { age:39 } // "object"

- typeof null // "object"   * A bug
- typeof [1,2,3] // "object"   * The array is a subtype of an object type

## Variables

- **A symbolic representation of data stored in the RAM**

```javascript
var name = "Kyle Simpson";  // the variable name is a symbolic representation of a cell of information in the RAM, that contains a set of bits representing the caracters together to form the string "Kyle Sympson"

var age;    // A location is reserved to store some information later
age = 39;   // We use the previously reserved space to set it a value

var friends = ["Brandon", "Marc"]   // The declaration of an array will reserve a whole section of memory

console.log(friends.length);    // console is also a variable. It refers to a Built-in function of JavaScript.
console.log(friends[1]):

// Assignments

var age = 39;   // age is 39
age++;  // age is 39 + 1
age += 2;   // age is 40 + 2

age;    // age is 42

// Expressions and statements

var age = 39;   // This is a statement. An assignment. 39 by itself is an expression.
age = 1 + (age * 2);    // This is an statement. Statements are built up with individual expressions.
```

## Decicions

```javascript

// Decisions

var isEnrolled = true;
if (isEnrolled) {
    console.log("Take the class!");
} else {
    console.log("Enroll first!");
}
```

## Loops

```javascript
// Loops

var students = ["Matt", "Sarah", "Susan"];

for (let i = 0; i < studens.length; i++) {      // Iterator
    greetStudent(students[i]);
}
for (let student of students) {
    greetStudent(student);
}

while (students.length > 0) {
    let student = students.pop();
    console.log(`Hello, ${student}!`);
}
```

## Functions

```javascript
// Functions

function greetStudent(student) {    // Takes some input and compute that input for us
    console.log(`Hello, ${student.name}!`);    // ``: interpolated strings -> to include other variables inside the string
}

function timeRemaining(timeElapsed, endTime) {
    return  endTime - timeElapsed;
}
var left = timeRemaining(42, 240);
left;
```

## First exercise

```javascript
// First exercise

function addFavoriteBook(bookName) {
    if (!bookName.includes('great')) {
        favoriteBooks.push(bookName);
    }
}

let favoriteBooks = [];

addFavoriteBook("Crime and punishement");
addFavoriteBook("The great Gastsby");
addFavoriteBook("You Don\'t Know JS");
addFavoriteBook("Sinuhe the egypcian");

function printFavoriteBooks() {
    console.log(`Favorite books: ${favoriteBooks.length}`);
    for (let book of favoriteBooks) {
        console.log(book);
    }
}

printFavoriteBooks();

```

## Types and coercion

```javascript
// Types and Coercion

// In JavaScript everything is an object (false)
// In JavaScript a variable has not type, the value do

var v;
typeof v;   // It returns 'undefined'

// JavaScript return undefined when a variable has not a value yet and even when a variable has not been declared at all.

var greeting = "Hello, class!";
var something = greeting / 2;

something;  // NaN (not a number)
Number.isNaN(something);    // true

// More built-in functions  - [new]
// They create representations of input values
/*
- Object()
- Array()
- Function()
- Date()
- RegExp()
- Error()

-> Don't use new:
    - String()
    - Number()
    - Boolean()

-> The way to convert from one type to another: coercion

- Number + Number = Number
- Number + String = String
- String + Number = String
- String + String = String

Falsy - Truthy

- ""        | - "foo"
- 0, -0     | - 23
- null      | - {a:1}
- NaN       | [1,3]
- false     | true
- undefined | function(){..}
                ...

*/

var yesterday = new Date("Feb 16, 2020");
yesterday.toUTCString();

// A quality JS program always embraces coercions, making sure the types involved in every operation are clear

// '==' allows coercion (types different)
// '===' disallows coercion (types same)

```

## Scope - closures

```javascript
// Scope-Closures

// Scope: where to look for things

var teacher = "Kyle";

function otherClass() {
    teacher = "Suzy";
    topic = "React";
    console.log("Welcome!");
}

otherClass();   // Welcome!

teacher;    // Suzy
topic;      // React

// Emptiness - undefined vs. undeclared
// Undefined (at least declared)

// Function Expressions : functions assigned as a value somewhere

var clickHandler = function() {     // Anonymous F-E

};
var keyHandler = function keyHandler() {    // Named F-E

}

// IFFE's   (Inmediately Invoked Function Expressions)

var teacher = "Kyle";
( function anotherTeacher() {
    var teacher = "Suzy";
    console.log(teacher);   // Suzy
}) ();  // With the parenthesis, the function is encapsuled so it has not a global scope
        // The parenthesis () at the end, indicates that the function will be executed inmediately after declaration

console.log(teacher);   // Kyle

// Instead of an IIFE we can use block scoping with let and braces:

var teacher = "Kyle";

{
    let teacher = "Suzy";
    console.log(teacher);
}

console.log(teacher);

// Tip: var at a function level and let at a block level


// Closure: allows to preserve access to a function variable so later it can be used

function ask(question) {
    setTimeout(function waitASec() {
        console.log(question);
    }, 100);
}
ask("What is closure?")
```

## This, Prototypes and classes

```javascript
/*
- this -> A function's this references the execution context for that call, determined entirely by how the function was call. A this-aware function can thus have a different context each time it's called, which makes it more flexible & reusable. (Dynamic context based upon how we call the function)

- Prototypes
- class{}
*/

var workshop = {
    teacher: "Kyle",
    ask(question) {
        console.log(this.teacher, question);
    },
};

workshop.ask("What is implicit binding?")

function ask(question) {
    console.log(this.teacher, question);
}

function otherClass() {
    var myContext = {
        teacher: "Suzy"
    };
    ask.call(myContext, "Why?"); // Suzy Why?
}

otherClass();


// Prototypes:

// We try to make something like a class:

function Workshop(teacher) {    // The constructor
    this.teacher = teacher;     // Is 'this' aware
}
Workshop.prototype.ask = function (question) {
    console.log(this.teacher, question);
                // deepJS.teacher | reactJS.teacher
}

var deepJS = new Workshop("Kyle");

/*
When using the keyword 'new', the object that is created is linked to the prototype. The object itself does not have a function ask
but as long as it's linked to the prototype of the 'class', it can use that function 'ask'.

The method ask is owned by the 'class' 'Workshop', and with the prototype we can delegate with any instance of the constructor the method to another object that is going to use it by its own purposes.

*/
var reactJS = new Workshop("Suzy");

deepJS.ask("Is 'prototype' a class?"); // Kyle Is 'prototype' a class?

reactJS.ask("Is 'prototype' a class?"); // Suzy Is 'prototype' a class?


// Class

class Workshop {
    constructor(teacher) {
        this.teacher = teacher;
    }
    ask(question) {
        console.log(this.teacher, question);
    }
}

var deepJS = new Workshop("Kyle");
var reactJS = new Workshop("Suzy");

deepJS.ask("Is 'prototype' a class?"); // Kyle Is 'prototype' a class?

reactJS.ask("Is 'prototype' a class?"); // Suzy Is 'prototype' a class?
```

### The book shelf excercise

```javascript

class bookShelf {
    constructor() {
        this.favoriteBooks = [];
    }
    addFavoriteBook(bookName) {
        if (!bookName.includes('great')) {
            this.favoriteBooks.push(bookName);
        }
    }
    printFavoriteBooks() {
        console.log(`Favorite books: ${String(this.favoriteBooks.length)}`);
        for (let book of this.favoriteBooks) {
            console.log(book);
        }
    }

}


function fakeAjax(url,cb) {
    setTimeout(function fakeLoadingDelay(){
        cb([
            "A Song of Ice and Fire",
            "The Great Gatsby",
            "Crime & Punishment",
            "Great Expectations",
            "You Don't Know JS"
        ]);
    },500);
}
function loadBooks(bookShelf) {
    fakeAjax(BOOK_API, function onBooks(bookNames){
        for (let bookName of bookNames) {
            bookShelf.addFavoriteBook(bookName);
        }
        bookShelf.printFavoriteBooks();
    });
}

var BOOK_API = "https://some.url/api";
var myBooks = new bookShelf();
loadBooks(myBooks);





```
