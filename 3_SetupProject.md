## Initial project Setup

Let’s start with creating an empty project file and initializing npm.

``` 
mkdir shardeum-nft-minter

cd shardeum-nft-minter

npm init
```

 Now, let’s install hardhat as a dev-dependency and choose ‘Create an empty hardhat.config.js’. This is also the right time to install the Openzeppelin Contracts Library all the other hardhat libraries we require.

``` 
npm install --save-dev hardhat

npx hardhat

npm install @openzeppelin/contracts

npm install --save ethers@5.7.2 hardhat @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers
```

With this, we have now completed our initial project setup and installed the smart contract dependencies. The next step is to write the smart contracts.