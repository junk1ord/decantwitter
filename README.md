# Decentratwitter

This is a Solidity smart contract that implements a decentralized version of Twitter called "Decentratwitter". Here's an overview of what each aspect of the code does:

- `SPDX-License-Identifier` is a comment at the top of the file that indicates the license under which the code is distributed. In this case, it's the MIT license.

- `pragma solidity ^0.8.0;` is a statement that specifies the version of Solidity the code is written in.

- import statements at the top of the file allow the contract to use code from external contracts. In this case, the contract imports code from the OpenZeppelin library for access control and the `ERC721URIStorage` contract for the implementation of the ERC721 token standard.

- The `contract Decentratwitter is ERC721URIStorage` line declares a new contract called Decentratwitter that inherits from the `ERC721URIStorage` contract. This means that Decentratwitter is an ERC721-compliant token contract that can be used to **represent unique, non-fungible assets on a blockchain**.

- `uint256 public tokenCount` declares a public state variable to **keep track of the number of tokens** that have been created by the contract.

- `uint256 public postCount` declares a public state variable to keep track of the **number of posts that have been created** by the contract.

- `mapping(uint256 => Post) public posts` declares a public mapping that associates post IDs with post data. Each post is represented by a struct that contains

  - an ID
  - a hash
  - a tip amount
  - the address of the author.

- `mapping(address => uint256) public profiles` declares a public mapping that associates user addresses with the IDs of the tokens they own. This is used to **determine which token a user has selected as their profile picture**.

- The `struct Post` declaration defines the Post data structure that contains

  - an ID
  - a hash
  - a tip amount
  - the address of the author.

- `event declarations` define **events that can be emitted by the contract**. In this case, there are two events: `PostCreated` and `PostTipped`.

- **The constructor function is called when the contract is deployed to the blockchain**. In this case, it sets the name and symbol of the ERC721 token.

- The `mint` function allows users to **mint new tokens**. It does the following:

  1. Increments the token count
  2. Mints a new token
  3. sets its URI
  4. associates it with the user's profile.

- The `setProfile` function allows users to **select a token as their profile picture**.

- The `uploadPost` function allows users to **create new posts**.

  - It checks that the user owns a token
  - makes sure the post hash exists
  - increments the post count
  - adds the post to the contract.
  - It also emits a `PostCreated` event.

- The `tipPostOwner` function allows users to **tip the author of a post**.

  - It checks that the post ID is valid
  - makes sure the user is not tipping their own post
  - sends Ether to the author
  - increments the tip amount
  - emits a `PostTipped` event.

- The `getAllPosts` function returns an array of all posts.

- The `getMyNfts` function returns an array of the IDs of all tokens owned by the caller.
