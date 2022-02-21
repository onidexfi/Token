# Paragen Token (RGEN) With Liquidity Protection Service

## Installation

    npm install
    npm run compile

## Testing on fork

    npm run test -- --network hardhat

## Deployment

Set bsc network node url and deployer private key in the .env file.

    npm run hardhat -- --network bsc deploy

## BSCscan verification

Set API key for bscscan in the .env file.
[https://bscscan.com/myapikey](https://bscscan.com/myapikey)

    npx hardhat verify --network bsc 0xTokenAddress

## Usage

Unblock accounts (must be done while protection is still on):

    npm run hardhat -- --network bsc unblock --token 0xTokenAddress --json ./blocked.example.json

Revoke tokens from blocked accounts (must be done while protection is still on):

    npm run hardhat -- --network bsc revoke-blocked --token 0xTokenAddress --to 0xRevokeToAddress --json ./blocked.example.json

Disable protection to make transfers cheaper:

    npm run hardhat -- --network bsc disableProtection --token 0xTokenAddress

Change the Liquidity Protection Service address:

    npm run hardhat -- --network bsc changeLPS --token 0xTokenAddress --lps 0xNewLpsAddress

---

## Paragen Token (RGEN) Protection parameters


User LiquidityProtectionsService address in the integrated token UsingLiquidityProtectionService.liquidityProtectionsService() override

    Current RGEN LiquidityProtectionsService address: 0x9786b0BeDC1fF41f4Dc1C471312ec1D179CBFa06

Switch off protection automatically on Sunday, March 27, 2022 11:59:59 PM GMT

[comment]: <> (>Epoch timestamp: 1648425599)

---
#####FirstBlockTrap On
block all users who buy tokens in the same block with pair creation transaction

---

#####LiquidityAmountTrap On
    LiquidityAmountTrap_blocks 7
    LiquidityAmountTrap_amount 37000
block every user who buys in total more than 37000 tokens during the 7 first blocks after pair creation

---

#####LiquidityPercentTrap On
    LiquidityPercentTrap_blocks 8
    LiquidityPercentTrap_percent 4%
block every user who buys more than 4% of current liquidity in one transaction, limitation works during the 8 blocks

---

#####LiquidityActivityTrap On
    LiquidityActivityTrap_blocks 6
    LiquidityActivityTrap_count 7
will block all users who buy tokens if in the same block was more than 7 transaction, limitation works during the 6 blocks

---

