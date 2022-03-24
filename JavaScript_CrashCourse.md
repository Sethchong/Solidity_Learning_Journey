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


### Callback 
```JS
/ callbacks

// callback is a function that passed as an argument to another function and this technique allows a function to call another function

// first make a const of arrays

const posts = [

{ title: 'Post one', body: 'this is post one' },

{ title: 'Post two', body: 'this is post two' }

];

// => means function (), they are both the same thing

function getPosts() {

setTimeout(() => {

let output = '';

// we want to loop through the posts here, gonna use for each method here

posts.forEach((post, index) => {

output += `<li> ${post.title} </li>`; // note that this is using a backtick, not ''

});

document.body.innerHTML = output;

}, 1000); // 1000 is in miliSec
}

function createPost(post, callback) {

setTimeout(() => {

posts.push(post);

callback();

}, 2000); // 2 seconds

}

// TLDR, without the callback function, JS will run the first function named getPosts and wont run the second fucnction

// by using callback on the second function, we are telling JS to run the 2nd function first then run the first function

createPost({ title: 'Post Three', body: 'This is post three ' }, getPosts);
```

callback allows us to basically to have the control to run certain function first, instead of by sequence 

***
### Promise 
#### https://javascript.info/promise-basics
a promise is basically a function that allows us to move on while waiting for an answer while not crashing or waiting for the webpage to load 

```js

// first make a const of arrays

const posts = [

{ title: 'Post one', body: 'this is post one' },

{ title: 'Post two', body: 'this is post two' }

];


// => means function (), they are both the same thing
  
function getPosts() {

setTimeout(() => {

let output = '';

// we want to loop through the posts here, gonna use for each method here

posts.forEach((post, index) => {

output += `<li> ${post.title} </li>`; // note that this is using a backtick, not ''

});

document.body.innerHTML = output;

}, 1000); // 1000 is in miliSec

}


function createPost(post) {

	return new Promise((resolve, reject) => {

	setTimeout(() => {

	posts.push(post);

	const error = false; // if its an error then define it as false

	if (!error) {

	resolve();

	} else {

	reject('Error: something went wrong!')
}}, 2000); // 2 seconds

});

}


createPost({ title: 'Post Three', body: 'This is post three ' }).then(getPosts);
```

So what is happening here is that once the code runs, it will wait for the `resolve()` to happen, once that is successful, it will run the `createPost()` function  at the end of the last line 

so if in the event if there is an error, it would be best to include a `.catch()` function to display a nicer error as follows: 
```js
createPost({ title: 'Post Three', body: 'This is post three ' }).then(getPosts).catch(err => console.log(err));
```

#### `Promise.all`
`Promise.all` is basically to return a list of promises such as below: 
```js
// Promise.all

const promise1 = Promise.resolve('Hello World');

const promise2 = 10;

const promise3 = new Promise((resolve, reject) =>
	setTimeout(resolve, 2000, 'Goodbye'));

  
Promise.all([promise1, promise2, promise3]).then(values => console.log(values));
```

*** 
### Async / Await 
this is just a cleaner way of doing promises 
```js
// first make a const of arrays

const posts = [

{ title: 'Post one', body: 'this is post one' },

{ title: 'Post two', body: 'this is post two' }

];

  

// => means function (), they are both the same thing

  

function getPosts() {

setTimeout(() => {

let output = '';

// we want to loop through the posts here, gonna use for each method here

posts.forEach((post, index) => {

output += `<li> ${post.title} </li>`; // note that this is using a backtick, not ''

});

document.body.innerHTML = output;

}, 1000); // 1000 is in miliSec

}

  

function createPost(post) {

return new Promise((resolve, reject) => {

setTimeout(() => {

posts.push(post);

  

const error = false;

  

if (!error) {

resolve();

} else {

reject('Error: something went wrong!')

}

}, 2000); // 2 seconds

});

}

  

// createPost({ title: 'Post Three', body: 'This is post three ' }).then(getPosts);

  

// Async / Await

// it is basically a more fancyful way to write promises

async function init() {

await createPost({ title: 'Post Three', body: 'This is post three ' });

getPosts();

}

  
init();

