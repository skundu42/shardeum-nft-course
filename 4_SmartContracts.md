## Smart Contracts

To build the NFT minter, we need to create a smart contract with the necessary logic to mint the NFT on-chain.

Solidity is an object-oriented, high-level language for implementing smart contracts on EVM. You can learn more about its syntax and language description from the [Solidity Docs](https://docs.soliditylang.org/en/v0.8.19/).


As we have already installed OpenZeppelin library, we will make use of its [ERC721](https://docs.openzeppelin.com/contracts/4.x/erc721) token format and one of its extension [ERC721URIStorage](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol) and only modify the changes we need, keping rest of the functionalities intact.


Create a **'contracts'** folder in your directory and add a file named **NftMinter.sol**

```
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.3;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
contract NFTMinter is ERC721URIStorage {

    constructor() ERC721("Shardeum Dev NFTMinter, "SNFT") {}

}

```

In the above code example, we have defined the basic contract strcuture, imported and inherited the ERC721URIStorage extension into our contract to use its fcuntionalities and set the Contract Name & Symbol.

To keep track of the tokenIDs, we can use the Counters library Openzeppelin provides.

```
import "@openzeppelin/contracts/utils/Counters.sol";

//Add inside contract
 using Counters for Counters.Counter;
 Counters.Counter private _tokenIds;

```

Now, the only fcuntionality we need to add is the ability to mint a new NFT with the input provided by the user on the fron-end into the URI and keep track of the respective tokenIDs.

Add the following code inside your contract:

```
function mintNFT(address recipient, string memory tokenURI) public returns (uint256) {
        _tokenIds.increment();
        uint256 newItemId = _tokenIds.current();
        _mint(recipient, newItemId);
        _setTokenURI(newItemId, tokenURI);
        return newItemId;
}
```

That's it! That's the only smart contract we will need in our NFT Minter application.



Here are some useful resources to leanr more about ERC721 NFT standard:


- https://ethereum.org/en/developers/docs/standards/tokens/erc-721/#:~:text=What%20is%20ERC%2D721%3F,something%20else%20like%20its%20visual.

- https://erc721.org/

