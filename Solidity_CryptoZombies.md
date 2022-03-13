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










