===========================
NFT Marketplace – Cyfrin Updraft Course Project
===========================

This repository contains two ERC721 NFT contracts: a Basic NFT and a dynamic on-chain SVG Mood NFT.
It also includes Foundry deployment scripts, interaction scripts, unit tests, and integration tests.


PROJECT SUMMARY

The project demonstrates:

ERC721 NFT minting (BasicNft)

Dynamic on-chain SVG NFTs (MoodNft)

Mood state flipping using owner-only logic

Base64 metadata construction

On-chain SVG rendering

Foundry-based deployment scripts

Interaction scripts for minting and flipping moods

Unit tests and integration tests verifying functionality

FEATURES:

Basic NFT

Standard ERC721 behavior

Public minting

Incremental token IDs

URI stored per token

Mood NFT

Fully on-chain SVG NFT

Dynamic tokenURI based on mood state

flipMood() function toggles between "happy" and "sad"

Only the owner of the NFT may change the mood

Token URI is generated in Base64-encoded JSON

SVG images embedded directly in metadata

Deployment Scripts

Deploys BasicNft

Deploys MoodNft

Compatible with local and live networks

Test Suite

Unit tests for each contract's logic

Integration tests covering minting + mood flipping

Deployment tests

Fuzz testing

State verification

Interaction Script

Mint NFTs using CLI

Flip NFT mood using CLI

PROJECT STRUCTURE

/
├── foundry.toml
├── lib/
├── script/
│ ├── DeployMoodNft.s.sol
│ ├── DeplyBasicNft.s.sol
│ └── Interactions.s.sol
├── src/
│ ├── BasicNft.sol
│ └── MoodNft.sol
└── test/
├── unit/
│ ├── BasicNftTest.t.sol
│ ├── MoodNftTest.t.sol
│ └── DeployMoodNftTest.t.sol
├── intergrations/
│ ├── BasicNftTest.t.sol
│ └── MoodNftIntergrationTest.t.sol
└── Interactions.s.sol

CONTRACT OVERVIEW
BasicNft.sol

A simple ERC721 minting contract.

Key functions:

mintNft() : Mints a new NFT

tokenURI(id) : Returns the stored metadata URI

Uses internal counter for token IDs

MoodNft.sol

Dynamic on-chain NFT with mood state.

Key features:

Stores "happy" or "sad" in a mood enum

flipMood(tokenId) toggles the mood

Only NFT owner may flip mood

tokenURI(tokenId) generates Base64 JSON metadata

Metadata includes SVG image encoded directly on-chain

TEST SUITE

Unit tests:

BasicNftTest.t.sol

Tests minting

Tests URI correctness

MoodNftTest.t.sol

Tests minting

Tests mood flipping

Tests permission checks

Tests dynamic tokenURI content

DeployMoodNftTest.t.sol

Verifies deployment script functionality

Integration tests:

BasicNFT integration test

MoodNFT integration test

Test full flow: deploy -> mint -> flip -> verify URI

Interaction script tests:

Demonstrates minting and flipping via CLI

To run all tests:
forge test -vv

DEPLOYMENT

Deploy BasicNft:
forge script script/DeplyBasicNft.s.sol --rpc-url $RPC_URL --private-key $PRIVATE_KEY --broadcast

Deploy MoodNft:
forge script script/DeployMoodNft.s.sol --rpc-url $RPC_URL --private-key $PRIVATE_KEY --broadcast

SECURITY CONSIDERATIONS

Ownership checks implemented for mood flipping

Require statements validate token existence

Uses OpenZeppelin ERC721 standard behavior

No reentrancy concerns in current form

Future marketplace addition must include proper withdrawal pattern, reentrancy guard, and access control

WHAT I LEARNED

On-chain SVG NFT design

Base64 metadata creation

State-driven dynamic NFTs

Foundry deployment scripting

Writing unit and integration tests

Foundry cheatcodes

Contract structure and modularity

Separation of concerns in smart contracts


ACKNOWLEDGEMENTS

This project was created while following the Cyfrin Updraft curriculum, I am new to solidity programing and so I would like to thank Patrick Collins for these amazing free resources. 
