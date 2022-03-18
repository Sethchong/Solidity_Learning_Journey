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
