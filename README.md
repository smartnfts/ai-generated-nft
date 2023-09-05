# Create and Mint NFT using AI

This project is forked from [dappuniversity/ai_nft_generator](https://github.com/dappuniversity/ai_nft_generator). The enhancements made are to be able to publish the smart contract and the NFTs on the Energi blockchain. Once published, the NFTs can be traded on the [GonnaMakeIt Marketplace](https://gonnamakeit.com).

## 1. Technology Stack & Tools

- Solidity (Writing Smart Contracts & Tests)
- Javascript (React & Testing)
- [Hardhat](https://hardhat.org/) (Development Framework)
- [Ethers.js](https://docs.ethers.io/v5/) (Blockchain Interaction)
- [React.js](https://reactjs.org/) (Frontend Framework)
- [NFT.Storage](https://nft.storage/) (Connection to IPFS)
- [Hugging Face](https://huggingface.co/) (AI Models)

## 2. Requirements For Initial Setup
- Install [NodeJS](https://nodejs.org/en/)

## 3. Setting Up
### 3.1. Clone/Download the Repository
```
git clone https://github.com/smartnfts/ai-generated-nft.git
```
### 3.2. Install Dependencies:
```
cd ai-generated-nft
npm install gh-pages --save-dev
```

### 3.3. Create APIs:

Create an account on [Hugging Face](https://huggingface.co/). Visit your profile settings, and create a `read` access token.

Create an account on [NFT.Storage](https://nft.storage/), and create a new API key.

### 3.4. Setup .env file:
Before running any scripts, create a `.env` file by copying `.env.example`. Edit the following:

- **ACCOUNT_PRIVATE_KEY=""** - Get the private key for your owner account from MetaMask
- **REACT_APP_HUGGING_FACE_API_KEY=""** - Populate the API from step 3 above
- **REACT_APP_NFT_STORAGE_API_KEY=** - Populate the API from step 3 above. Do not put any quotes around the API

### 3.5. Name your collection

Edit lines 4, 5 and 6 of `scripts/deploy.js`:

```
  const NAME = "AI Generated NFT"
  const SYMBOL = "AINFT"
  const COST = ethers.utils.parseUnits("0.5", "ether") // 0.5 NRG
```

- *NAME* - Name of collection as you want it to appear on the Marketplace
- *SYMBOL* - Token Symbol of your collection
- *COST* - Minting cost


### 3.6. Update Constructor Arguments

Edit `scripts/constructor-arg.js`. 

```
module.exports = [
    "AI Generated NFT", 
    "AINFT", 
    "1"
];
```

The entires should match the information set in `scripts/deploy.js` in step 5 above.


### 3.7. Run deployment script

Deploy the smart contract to Energi Testnet.

```
npx hardhat run ./scripts/deploy.js --network energiTestnet 
npx hardhat verify <contract_address> --constructor-args ./scripts/constructor-arg.js
```

### 3.8. Start frontend

```
npm run start
```

The above will start a web browser instance. If you are using the `Brave Browser`, turn shield off to "http://localhost:3000".


## 4. Create and Mint AI Generated NFT

- *4.1.* Connect your Owner Wallet
- *4.2.* Give a `name` for the image
- *4.3.* Add a `description` to your NFT. The AI NFT Generator will take the description and create an NFT. 
- *4.4.* Click "Create & Mint" to generate an NFT using the AI, post the NFT to IPFS and mint it on the Energi Blockchain. You will have to pay the minting cost. 

![Webpage](src/assets/img/webpage.png)

Once minted the image of the NFT will appear on the box to the right. Go to [GMI Testnet Marketplace](https://nrg.test.gonnamakeit.com) to view your collection.

Have fun with your NFTs!

## 5. Detailed Video on Coding

For details on how the code works, view the following YouTube video:
- [Code an A.I. NFT Minting App With Stable Diffusion Step-by-Step](https://www.youtube.com/watch?v=myascjqPnFc).

## 6. Contributions

Please send any contributions as ETH (on the Ethereum chain) or NRG (on the Energi chain) to the following account:

```
0x3E9764ee008697849292511d278E8a05e1Fbba27
```
