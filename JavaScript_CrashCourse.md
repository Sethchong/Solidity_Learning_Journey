### Basic Crashcourse
```` javascript
// console.log acts like a print in JS 
console.log('Hello World!');

// to define a variable
// rules to name a variable is pretty similar as the rest of programming languages
let a_name = 'seth';
console.log(a_name);

// assinging a constant 
const interestRate = 0.3;
console.log(interestRate);


// there are 2 main different types of data - Value VS Reference types 

// Value type includes the following: 
// String / number / boolean / undefined / null 

let name = 'Seth Chong'; // string
let age = 25; // number 
let isApproved = true; // boolean 
let firstName = undefined;
let selectedColor = null;

// Reference type inlcudes the following: 
// object / Array / Function

let person = {
    name: 'Chong',
    age: 23
};              // this is how you define an object 

console.log(person);

// so what happens if we want to change the name of the person? 
// we can do it in 2 ways: dot notation VS bracket notation

// dot notation
person.name = 'john';

// bracket notation allows us to be more dynamic and users can choose different names afterwards 
let selection = 'name';
person[selection] = 'james';

// functions 
// the name inside greet is called the parameter
function greet(name) {
    console.log('Hello ' + name);
}

// seth inside greet is called argument
greet('Seth');

// if we want to set up a function to calculate something 
function square(number) {
    return number * number;
}
let number = square(100);
console.log(number);

````

### What is HTML DOM? 
it is essentially an Object Model for HTML and it defines HTML elements as object
in other words, HTML DOM is the standard for how to get, change, add or delete html elements 

HTML DOM methods are **actions** you can perform 
HTML DOM properties are **values** that you can set or change 

```html
<html>  
<body>  
  
<p id="demo"></p>  
  
<script>  
document.getElementById("demo").innerHTML = "Hello World!";  
</script>  
  
</body>  
</html>
```

```getElementById```  is a method while ```innerHTML``` is a property 
recall that``` id = 'demo'``` is something like a class - it is meant to use that for some basic formatting 

### https://www.w3schools.com/js/js_htmldom_document.asp
### https://www.youtube.com/watch?v=y17RuWkWdn8

```js
const body = document.body
const div = document.createElement('div')
div.innerText = "Hello World"

body.appendChild(div)
// take note that appendchild allows you to append only elements! not Strings! dont confuse it with append. 
// append can append strings directly 
```


### Callbacks, Promises, Async, Await Crashcourse

so sometimes we want to extract something from the server and it would get a couple of seconds for the data to return to us but we also don't want to stall while we wait for the data and we want to continue and keep doing something 



```` javascript
// callbacks / promises / async / await 


````



























