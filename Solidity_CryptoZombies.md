## Introduction 
A contract is the fundamental building block of Eth's applications - all variables belong to a contract
  
All solidity source code should start with a "version pragma" a declaration of the
version of the Solidity compiler this code should use. 
  
This is to prevent issues with future compiler versions potentially introducing changes that would break your code

#### uint
uint is unsigned integers and it is a data type that as to be non-negative 

in Solidity, uint is actually an alias for uint256, a 256-bit unsinged integer - you can also declare units with less bits too - uint8, uint16, uint32

#### Arrays 

there are fixed arrays and dynamic array 
```` solidity
// Array with a fixed length of 2 elements:
uint[2] fixedArray;
// another fixed Array, can contain 5 strings:
string[5] stringArray;
// a dynamic Array - has no fixed size, can keep growing:
uint[] dynamicArray;
````
we can also create an array of structs too such as: 
```` solidity 
Person[] people; 
// [] means is a dynamic array and the name of it is people
````

<a href = "http://extropy.foundation/workshops/bootcamp/soliditytutorial.html#:~:text=Definiton%20%3A%20In%20Solidity%2C%20a%20getter,between%20parentheses%20for%20example%20(%20uint%20)"> Link to getter explanation </a>

#### <a href ="https://www.geeksforgeeks.org/storage-vs-memory-in-solidity/#:~:text=Much%20like%20RAM%2C%20Memory%20in,off%20for%20the%20next%20execution."> Memory VS Storage </a>
memory is a temporary place to store data whereas storage holds data between function calls 

Well, there are two ways in which you can pass an argument to a Solidity function:

- By value, which means that the Solidity compiler creates a new copy of the
parameter's value and passes it to your function. This allows your function to
modify the value without worrying that the value of the initial parameter gets changed.

- By reference, which means that your function is called with a... reference to the
original variable. Thus, if your function changes the value of the variable it
receives, the value of the original variable gets changed.


#### Adding new items to the arrays
```` solidity
// create a New Person:
Person satoshi = Person(172, "Satoshi");

// Add that person to the Array:
people.push(satoshi);

// combining into 1 line of code:
people.push(Person(16, "Vitalik"));
````

```` Solidity
// create a struct
struct Zombie {
        string name;
        uint dna;
    }
    // create an array and call it zombies
    Zombie[] public zombies;

    // create a function to add new item to the array - taking input from the function arguments
    function createZombie (string memory _name, uint _dna) public {
        // start here
        zombies.push(Zombie(_name, _dna));
    }

````

#### More on functions 

#### Function modifiers 
The above function doesn't actually change state in Solidity ??? e.g. it doesn't change any values or write anything.

So in this case we could declare it as a view function, meaning it's only viewing the data but not modifying it:
```` solidity 
function sayHello() public view returns (string memory) {
````

there is also pure function which menas you;re not even accessing any data in the app
```` solidity 
function _multiply(uint a, uint b) private pure returns (uint) {
  return a * b;
}
````
The function doesn't even read from the state of the app - its return value depends only on its function paramters. So in this case we would declare the function as ```pure```

```` solidity
// we want to make a private function and it will take a parameter named _str which is stored to memory and return a uint 
    function _generateRandomDna(string memory _str) private view returns (uint){
    }
````








