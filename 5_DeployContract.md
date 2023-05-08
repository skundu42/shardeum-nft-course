## Deploy your Smart contracts using Hardhat

Create a ***'scripts'*** folder in your directory and create a file named **deploy.js**.

The script uses the ethers  library to deploy the smart contract and print out the contract address in the console.

```
const { ethers } = require("hardhat");

async function main() {
    const NFTMinter = await ethers.getContractFactory("NFTMinter");
    const nftMinter = await NFTMinter.deploy();
    await nftMinter.deployed();
    console.log("NFTMinter deployed to:", nftMinter.address);
  }

    main()
    .then(() => process.exit(0))
    .catch((error) => {
      console.error(error);
      process.exit(1);
    });

```

Now that we have the deploy script ready, its time to configure our hardhat config file with the Shardeum network details.

```
require("@nomiclabs/hardhat-waffle");
module.exports = {
  networks: {
    hardhat: {
    },
    liberty: {
      url: "https://liberty20.shardeum.org/",
      accounts:[``] // Add private key here
    },
    sphinx: {
        url: "https://sphinx.shardeum.org/",
        accounts: [``] // Add private key here
        }
  },
  solidity: "0.8.3",
};

```

Please make sure you remove any private keys before pushing your code in github. Preferably you may also use a library like [dotenv](https://www.npmjs.com/package/dotenv) to handle your private keys. 

Make sure you have [Testnet SHM](https://docs.shardeum.org/faucet/claim) in the wallet your are using.

Now, we have everything ready to deploy our smart contract. 

```
npx hardhat run scripts/deploy.js --network sphinx
```

Keep note of the deployed smart contract. We will use it in our next step while interacting with the smart contract.