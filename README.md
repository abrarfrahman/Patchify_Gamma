# Patchify Whitepaper

_A decentralized, democratic platform built to empower trustless professional networking._

Final Deliverable for IndEng 185 @ UC Berkeley: Blockchain Challenge Lab 

Contributors: *Abrar Rahman, Armand Bechy*

## Introduction
Curating your digital professional presence is a universal headache in the modern era. Jumping through the hoops of the recruiting process often forces my peers to “out-lie” each other, exaggerating qualifications because 1) there are no consequences for doing so, and 2) everyone embellishes their skills. What if there was a way to leverage emerging technologies to disrupt recruiting, bringing hiring back to a fact-based, qualification-driven ideal?

The Patchify Protocol verifies coursework and microskills earned from partner organizations through an immutable ledger and NFT portfolio solution (PatchLets). It also solves for corruption in centralized social media platforms, allowing users to stake a fungible reputation-based governance token (PatchUps) which represents literal investments in professional connections while granting voting power and other privileges on the site.

The team is working towards creating a professional network with companies and dencentrally moderated single-interest groups alike, a dynamic online community that incorporates elements of LinkedIn, Reddit, and Blind.

## Value Propositions for Stakeholders
### IT Firms & Recruiters
- A verified, trustworthy pool of talent, as NFT course certifications can only be issued by accredited educational institutions
- PatchLets microskill tree clusters allow recruiters to assess the skills and coursework experience of candidates with unprecedented granularity
- Integration with proof-of-attendence protocols (POAPs)
- EdTech protocol enables fast deployment of training materials tied to proprietary, in-house technologies

### Candidates / Classic Userbase
- Trustless verification of certificate programs occurs on-chain. You own your certificates forever, even if Patchify ceases to exist
- Allows candidates to protect their data and (optionally) maintain anonymity
- Enables qualification-driven, double-blinded recruiting to level the playing field for underrepresented minorities
- PatchUps governance tokens grants privileges to individual users to shape the direction of the protocol going forward 

### Partnering Educational Institutions
- Integration with Patchify Protocol makes achievements from EdTech platforms publicly-accessible and verifiable
- Tokenization enhances gamified approaches to teaching by adding real stakes to the learning process, encouraging completion and competition
- A token/NFT economy supports digital learning creators by establishing a supplemental cash flow model that is cross-compatible with freemium or subscription based plans

## Patchify Tokens
Naming convention is inspired by the Boy/Girl Scouts of America and their practice of recording achievements via sewn fabric patches.

### PatchLets: A Composable Standard for Certification Verification

There are four distinct kinds of proof-of-skill NFTs compatible with the protocol. Visualizations are minted via ERC-721 tokens.

1. Degrees issued by partnering colleges and universities using BlockCerts (https://www.blockcerts.org/)
2. Standalone Course PatchLets
3. Microskill Tree Clusters
    1. Can be set up with dependencies (“prerequisites”) between one another, which can be displayed on the Portfolio page as a skill tree composed of Patchlets. 
    2. For example, we envision Patchlets being used for tracking microskills or coursework before unlocking a full certificate/degree, or nested Patchlets that unlock completion for a given assignment instead of a new course, etc. 
    3. If desired, institutions can embed metadata about course completion metrics (ex: time, grade, absences) in a visualizable fashion when generating the NFT. The options are limitless.
4. Certificates / POAPs

Private keys for PatchLets are stored in the user’s crypto wallet of choice. Users will be able to decide whether a given certificate is publicly viewable in the Portfolio Manager, though the verification for completing a given course can be done without this public view seeing as all transactions, and thus all records for course completion, are immutably stored on the blockchain. These PatchLets can be issued by accredited educational institutions, Patchify itself, or third parties. Patches are non-transferable but will be made public-access through the Profile page, which includes an optional social profile as well as a Portfolio to showcase skills/courses. 

In order to set up the xPatch marketplace, all that is necessary is to implement the OpenSea SDK. OpenSea is the largest decentralized marketplace for the sale of NFTs, with a total of 80 million digital goods available with a total market value of above $10 billion. OpenSea is scalable, trustworthy, and established, making it a perfect fit.

It is preferable to implement the OpenSea SDK instead of forking the whole service because while an education marketplace has many requirements that do not match the design of an open auction site, we want to retain any security upgrades made by the OpenSea team, and regardless any additional functionality can be accomplished via embedded metadata verification. For instance, on OpenSea, any wallet address can serve as a buyer or seller. However, we want a clear separation between the “Educational Institution” and “Student” roles, so when a user first attaches their crypto wallet to the service, all metadata recorded on-chain will be flagged with that role. Moreover, there is no secondary market for Patches, as each NFT represents an individually tied achievement. These are one-time certificates that may or may not be issued with an expiration date. However, the ERC-721 standard for NFTs does not allow for these kinds of restrictions. Thus, the way to bind these certificates deterministically and permanently to the student that earned it is to embed a hash of the wallet address on the NFT itself so Patchify’s Portfolio View can verify and only display original certificates.

### PatchUps: Decentralized Governance for Professional Networking

PatchUps are non-transferrable, and can only be accumulated via Endorsements from collaborators, supervisors, or even a DAO. They are not meant to be used as a true currency, and cannot be swapped back for wETH. An Endorsement is a smart contract that requires the granter to stake some of their own reputation and permanently disclose a business relationship in order to complete the transaction. 

Endorsement metadata is an on-chain immutable ledger that reflects the nature of the relationship, the current state of the PatchUp reputation of both parties, and the level of endorsement (scaled by some factor as a function of reputation). Ensuring the transactions reflect meaningful business relationships is key. It must cost reputation to endorse others, though not necessarily scaled 1:1, with liquidity pools of stablecoins ensuring that we can work along any point of the token bonding curve. PatchUps can either be tied to the user (General Endorsement) or to a Patch (Skill Endorsement). Endorsements ought to be rate-limited by the state machine’s inbox.

PatchUp tokens serve as the bedrock for the broader solution for professional social networking that Patchify proposes. Existing social media firms such as LinkedIn or Facebook are incredibly centralized. This creates a perverse incentive structure where the user data/content is the backbone for a big-data firm’s business model, but those who provide this data capital in the first place have little to no say in how their data is tracked, shared, or used. 

In order to return power back to the communities which provide social media its value, PatchUp tokens serve as a voting mechanism to ensure consensus around any community-level changes on the moderation standards, technology stack, or business model for Patchify. Moreover, investors can use the PatchUp ledger as an additional data point for risk assessment as a proxy for institutional support within DAOs. After all, the market capitalization and number of participants in a DAO is a poor metric for its trustworthiness, but the participation of experienced and trusted individuals might be worth considering.

The PatchUp ERC-20 token will be built on the Arbitum L2 (https://arbitrum.io/) chain for effortless scaling, accessibility of documentation and community support, and broad compatibility with the Ethereum ecosystem. For one, the Arbitum Bridge (https://bridge.arbitrum.io/) includes integrations with MetaMask and Coinbase Wallet. But the utility of this framework goes far beyond mere token swapping. We are also considering using existing reputation tokens such as Orange Protocol (https://www.orangeprotocol.io/).

A Layer 2 trusted architecture allows the Arbitum Virtual Machine (AVM) to more efficiently compute and store smart contacts instead of directly running on the rate-limited Layer 1 EVM. This makes intensive computational tasks much easier to optimize and gives developers flexibility to customize the feature set for their particular chain. In order to do so in a transparent and trustless manner, the AVM needs to support both the execution and proving the contracts’ validity to the L1 chain. But these functionalities are seperated, so that few contracts ever actually need to be verified, though the proofs are in place ready to be executed, allowing for high throughput. Through a system of tupleization, all data on the AVM can be efficiently hashed and thus Merkleized, both for local execution and for the on-chain state machine.


## Minimum Viable Product & Go-to-Market Strategy
For a minimum viable product (MVP), Patchify ought to pursue a partnership with an established name in the EdTech space in order to get constructive feedback on the Patch system before expanding to the general public. For example, Khan Academy already has extensive course materials, strong brand recognition among our target demographic, and content organized for their internal gamification system. By giving users the opportunity to verifiably present their work to potential employers, Patchify stands to give all stakeholders in the certification and recruitment processes significant value.

### Pseudonymous Social Profile
A unique advantage for our professional network is that it allows users to remain anonymous. Your Patchify Profile is associated with your preferred in-browser crypto wallet, and thus no obligation exists to reveal identity. Moreover, the very advantage of establishing a professional network as a dApp is that we can leverage decentralized trust to ensure that the achievements listed are still valid. This is key for reaching our target demographic. This enables double-blinded, qualification-based, bias-free talent searches.

### DisPatch Messaging
Patchify incorporates an internal end-to-end encrypted messaging service, using the beta release of Blockscan (https://chat.blockscan.com/). We also offer compatibility with the platforms most popular among Web3 workers such as Telegram, Signal, Twitter, or Discord. Building on the existing channels of communication within the crypto community is key to ensure that users face the fewest barriers possible to adopting the Patchify Protocol as their portfolio solution of choice.

## Development Tools
For front-end development, the React Native library for JavaScript (https://reactnative.dev/) seems like a natural fit. React is one of the most commonly-used JavaScript libraries in the status quo. React Native allows for native web applications to render natively on both iOS and Android from a single codebase, an efficient cross-platform solution. Though developers will write the app in JS, it will only render as such on web browsers—the Android app refactors to Kotlin, while the iOS app runs lightning-fast in Swift. To help expand crypto adoption beyond niche enthusiast communities, we adopt a mobile-first approach, and React Native is a key part of implementing that strategy.

Solidity is an object-oriented, high-level language which is run on the EVM [20]. This is the key language for developing anything in the Ethereum ecosystem. In order to integrate these Web2 technologies with composable Web3 infrastructure, we turn to the Web3.js library (https://web3js.readthedocs.io/en/v1.7.3/), turning our React Native application into a dApp and serving as the starting point for deeper integrations with Web3 protocols.

For the development framework, asset pipeline, and testing environment, we opt to use the Hardhat suite (https://hardhat.org/), which offers a rich set of tools for developing Ethereum smart contracts. This allows us to develop a comprehensive set of unit tests for our app which can easily be run with command-line tools. To test on-chain functionality without spending gas on immutable changes to the Ethereum blockchain, we will use the Rinkeby testnet (www.rinkeby.io/).  
