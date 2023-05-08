##  NFT Minter Front-end

Now, let’s create a basic front-end application to interact with our deployed smart contract. 

Let’s start with initializing a react-application in the same folder. After the react application is set-up, also install all the necessary front-end packages.

```
npx create-react-app .
npm install @emotion/react @emotion/styled @mui/material axios

```

We will make all our front-end code changes in the src folder. Locate ***NFTMinter.json*** file from your artifacts folder and bring it to the src folder.

In the ***src*** folder, we need to work on 4 seperate javascript files.