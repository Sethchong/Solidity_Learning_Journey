### Learning Solidity and ETH Smart Contract 

https://app.buildspace.so/projects/CO02cf0f1c-f996-4f50-9669-cf945ca3fb0b/lessons/LE8f43618f-ffae-44ef-892b-2600adb2eba7

### Questions that need answering: 

1. what is a node? why we do we need to use node.js? 
    - it is a RTE for executing JS 
    - often used to build back-end services such as API 
    - the main benefits are it is superfast and highly scalable and great for prototyping in an agile dev  
2. what is runtime environment (RTE)
    - it is the env in which a program or app is executed - that is also why sometimes you get runtime errors 
3. So why do we need to use Node.js and JS with eth? 
    - we use Node.js to interact with our local eth node and this is also how we can pass information about the smart contract to our Node.js application 






### Set up for Hardhat 

First you have to install npm LTS package - https://nodejs.org/en/
choose the LTS package 

then type in 
````
npm install --save-dev- hardhat
<after installing - you can run hardhat using npx>
npx hardhat 
````

So in this case, i have tried to use Node Version Manager (nvm) 
```` terminal
$ git clone git://github.com/creationix/nvm.git ~/.nvm

curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.35.2/install.sh | bash

nvm install 12

nvm use 12

nvm alias default 12

npm install npm --global # Upgrade npm to the latest version
````

#### Constructor funtion

Constructor is called when a contract is first created and can be used to set initial values. 

##### so when do we need to use it? 
When a contract is created on the block chain you can use the constructor to set state variables. For example when deploying your contract you can set:  

Contract Owner – you can set the owner address at creation time
Max amount – set the maximum amount of a token
True or false values
Any parameter that you want to save

Constructor is a special function declared using constructor keyword. It is an optional funtion and is used to initialize state variables of a contract. Following are the key characteristics of a constructor.

    - A contract can have only one constructor.

    - A constructor code is executed once when a contract is created and it is used to initialize contract state.

    - After a constructor code executed, the final code is deployed to blockchain. This code include public functions and code reachable through public functions. Constructor code or any internal method used only by constructor are not included in final code.

    - A constructor can be either public or internal.

    - A internal constructor marks the contract as abstract.

    - In case, no constructor is defined, a default constructor is present in the contract.













