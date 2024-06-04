# myToken.sol

## Overview

`MyToken.sol` is a simple ERC20-like token contract written in Solidity. This contract allows for minting and burning of tokens, keeping track of balances and total supply. 

## Contract Features

### Public Variables
The contract has three public variables that store the details about the token:
- `tokenName`: The name of the token (e.g., "META").
- `tokenAbbrev`: The abbreviation of the token (e.g., "MTA").
- `totalSupply`: The total supply of tokens in circulation.

### Mapping
A mapping is used to keep track of the balances of each address:
- `balances`: Maps an address to its token balance (address => uint).

### Mint Function
The `mint` function allows for the creation of new tokens. It takes two parameters: an address and a value. This function increases the total supply by the specified value and also increases the balance of the specified address by the same amount.

```solidity
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
```

### Burn Function
The `burn` function allows for the destruction of tokens. It takes two parameters: an address and a value. This function decreases the total supply by the specified value and also decreases the balance of the specified address by the same amount, provided the address has sufficient balance.

```solidity
function burn(address _address, uint _value) public {
    if (balances[_address] >= _value) {
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}
```

## Requirements

1. **Public Variables**: 
   - `tokenName` stores the name of the token.
   - `tokenAbbrev` stores the abbreviation of the token.
   - `totalSupply` stores the total supply of tokens in circulation.

2. **Mapping**: 
   - `balances` maps an address to its token balance.

3. **Mint Function**: 
   - Takes an address and a value.
   - Increases the total supply by the specified value.
   - Increases the balance of the specified address by the same amount.

4. **Burn Function**: 
   - Takes an address and a value.
   - Decreases the total supply by the specified value.
   - Decreases the balance of the specified address by the same amount, provided the address has sufficient balance.

5. **Burn Function Conditionals**: 
   - Ensures that the balance of the sender is greater than or equal to the amount to be burned.

## Usage

### Deploying the Contract
Deploy the contract using your preferred Ethereum development environment (e.g., Remix, Truffle, Hardhat).

### Interacting with the Contract
- **Minting Tokens**: Call the `mint` function with the recipient's address and the number of tokens to mint.
- **Burning Tokens**: Call the `burn` function with the address from which tokens will be burned and the number of tokens to burn.

### Example
```solidity
// Minting 100 tokens to address 0x123...
myToken.mint(0x123..., 100);

// Burning 50 tokens from address 0x123...
myToken.burn(0x123..., 50);
```

## License

This contract is licensed under the MIT License. See the `LICENSE` file for more details.
