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





