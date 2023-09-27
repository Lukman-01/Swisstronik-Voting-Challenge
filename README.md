 # Voting Smart Contract Documentation

This documentation provides information on the deployment and usage of the "Voting Smart Contract" on the Swisstronik Testnet using the Hardhat development environment.

## Table of Contents

- [Overview](#overview)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Deployment](#deployment)
- [Interacting with the Contract](#interacting-with-the-contract)
- [Additional Information](#additional-information)
- [License](#license)

## Overview

The "Voting Smart Contract" is designed for managing candidates and voters in an election on the Ethereum blockchain. It allows candidates to be added, voters to be registered, and votes to be cast. This documentation provides instructions on how to deploy and interact with the contract on the Swisstronik Testnet.

## Getting Started

### Prerequisites

Before deploying the contract, ensure you have the following prerequisites in place:

1. [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/) installed on your machine.

2. A Swisstronik Testnet account with some test Ether (ETH) for contract deployment. You can obtain test Ether from a Swisstronik Testnet faucet.

3. A development environment such as [Hardhat](https://hardhat.org/) installed.

4. Create a `.env` file in your project root directory and add your private key as follows:

   ```
   PRIVATE_KEY=<YOUR_PRIVATE_KEY>
   ```

### Deployment

To deploy the "Voting Smart Contract" on the Swisstronik Testnet, follow these steps:

1. Clone this repository to your local machine and navigate to the project directory.

2. Install the project dependencies by running:

   ```
   npm install
   ```

3. Update the Hardhat configuration file (`hardhat.config.js`) with your Swisstronik Testnet URL and private key.

   ```javascript
   networks: {
     swisstronik: {
       url: "https://json-rpc.testnet.swisstronik.com/",
       accounts: [`0x${PRIVATE_KEY}`],
     },
   },
   ```

4. Deploy the contract to the Swisstronik Testnet by running the following command:

   ```
   npx hardhat run scripts/deploy.js --network swisstronik
   ```

   This command will deploy the contract and display the deployment address.

## Interacting with the Contract

After deploying the contract, you can interact with it using Ethereum wallets or dApp front-ends. Here are some common interactions:

- **Contract Owner Actions:**
   - The contract owner can add candidates using the `setCandidate` function.
   - The owner can register voters using the `registerVoter` function.

- **Registered Voter Actions:**
   - Registered voters can cast their votes using the `vote` function.
   - They can check if they have already voted using the `voters` mapping.

- **Data Retrieval:**
   - Retrieve candidate data using the `getCandidateData` function.
   - Retrieve voter data using the `getVoterData` function.
   - Get the list of registered candidates and voters using respective functions.
   - Obtain the current vote count for each candidate using the `getVoteCount` function.

## Additional Information

- This contract uses OpenZeppelin libraries for access control, counting operations, and safe arithmetic.

- Ensure that the contract owner responsibly manages voter registrations and candidate additions.

- The contract can be further extended with additional features, such as timestamping votes or adding more access control.

## License

This smart contract is open-source and released under the MIT License.