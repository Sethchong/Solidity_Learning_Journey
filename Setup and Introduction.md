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

### run.js first version 

```` javascript 

// writing a script to run our contract - because to test a smart contract we have to compile, deploy then execute 

const main = async () => {
    // this will actaully compile our contract and generate the necessary files we need to work with our contract under the artifacts directory.
    const waveContractFactory = await hre.ethers.getContractFactory ("WavePortal");

    // What's happening here is Hardhat will create a local Ethereum network for us, but just for this contract. Then, after the script completes it'll destroy that local network. So, every time you run the contract, it'll be a fresh blockchain. What's the point? It's kinda like refreshing your local server every time so you always start from a clean slate which makes it easy to debug errors.
    const waveContract = await waveContractFactory.deploy();

    // we will wait til our contract is officially deployed to our local blockchain! our constructor runs when we actually deploy
    await waveContract.deployed();

    // Finally, once it's deployed waveContract.address  will basically give us the address of the deployed contract. This address is how we can actually find our contract on the blockchain. There are millions of contracts on the actual blockchain. So, this address gives us easy access to the contract we're interested in working with! This will be more important a bit later once we deploy to a real Ethereum network.
    console.log("Contract deployed to:", waveContract.address);
};


const runMain = async ( ) => {
    try {
        await main () ;
        process.exit(0); // exit Node process without error
    } catch (error) {
            console. log (error);
            process.exit(1); // exit Node process while indicating 'Uncaught Fatal Exception' error
    }
// Read more about Node exit ('process. exit (num)') status codes here: https://stackoverflow.com/a/4716
};
runMain();

````

### Writing version 2 (documenting a wave)

### Solidity
```` solidity
/ writing the smart contract

// we want to be able to let someone wave at us and then store that wave - so we need to write a function to allow them to hit to wave at us 

pragma solidity ^0.8.0; 

import "hardhat/console.sol";

contract WavePortal {

    uint256 totalWaves;

    // constructor is a special function that uses 
    constructor(){
        // console.log is also used in JS and the main function is to print any kind of variables defined before in it or to just print any message that needs to be displayed to the user 
        console.log("Hello! I am a contract and I am smart!");
    }

    // writing a function to so that people can start waving at us 
    function wave() public {
        
        // recall that we have previously defined totalWaves to be uint and this is a state variable that is automatically initalized to 0 
        // recall that state variable is a variable with values that are permanently stored in a contract storage 
        totalWaves += 1;

        // msg.sender acts like a built-in authentication! because this is the wallet address of the person who has called the function 
        // this allows us to know exactly who called the function because in order to even call a smart contract function, you need to be connected with a valid wallet
        console.log("%s has waved!", msg.sender);
    }

    function getTotalWaves() public view returns (uint256) {
        console.log("We have %d total waves!", totalWaves);
        return totalWaves;
    }


}

````
### Javescript 
```` javascript

// writing a script to run our contract - because to test a smart contract we have to compile, deploy then execute 

const main = async () => {
    // In order to deploy something to the blockchain, we need to have a wallet address! Hardhat does this for us magically in the background, but here I grabbed the wallet address of contract owner and I also grabbed a random wallet address and called it randomPerson. This will make more sense in a moment.
    const [owner, randomPerson] = await hre.ethers.getSigners();


    const waveContractFactory = await hre.ethers.getContractFactory("WavePortal");

    const waveContract = await waveContractFactory.deploy();

    await waveContract.deployed();


    console.log("Contract deployed to:", waveContract.address);

    // this is just to see the address of the person deployingour contract! 
    console.log("Contract deployed to:", owner.address);


    // Basically, we need to manually call our functions! Just like we would any normal API. First I call the function to grab the # of total waves. Then, I do the wave. Finally, I grab the waveCount one more time to see if it changed.
    let waveCount;
    waveCount = await waveContract.getTotalWaves();

    let waveTxn = await waveContract.wave();
    await waveTxn.wait();

    waveCount = await waveContract.getTotalWaves();

    waveTxn = await waveContract.connect(randomPerson).wave();
    await waveTxn.wait();

    waveCount = waveContract.getaTotalWaves();
};


const runMain = async ( ) => {
    try {
        await main () ;
        process.exit(0); // exit Node process without error
    } catch (error) {
            console. log (error);
            process.exit(1); // exit Node process while indicating 'Uncaught Fatal Exception' error
    }
// Read more about Node exit ('process. exit (num)') status codes here: https://stackoverflow.com/a/4716
};
runMain();

````












