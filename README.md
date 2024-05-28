# DegenToken

DegenToken is an ERC20 token smart contract implemented in Solidity. It serves as the currency for an in-game ecosystem, allowing users to transfer tokens, mint new tokens (only callable by the owner), and redeem tokens for items in the in-game store.

## Features

- **ERC20 Compliance**: DegenToken follows the ERC20 standard, providing basic functionality such as transferring tokens and querying token balances.
- **Minting**: The contract owner can mint new tokens, increasing the token supply.
- **Burning**: Users can burn (destroy) tokens, reducing the total token supply.
- **Redemption**: Users can redeem tokens for items in the in-game store, triggering an event to log the redemption.

## Usage

### Minting Tokens

The owner of the contract can mint new tokens using the `mint` function, specifying the recipient's address and the amount of tokens to mint.

```javascript
function mint(address to, uint256 amount) external onlyOwner {
    _mint(to, amount);
}
```

## Transferring Tokens

Users can transfer tokens to another address using the transfer function.

```javascript
function transfer(address to, uint256 amount) public override returns (bool) {
    require(amount <= balanceOf(msg.sender), "Insufficient balance");
    _transfer(msg.sender, to, amount);
    return true;
}
````

## Redeeming Tokens

Users can redeem tokens for items in the in-game store using the redeem function.

```javascript
function redeem(uint256 amount) external {
    require(amount <= balanceOf(msg.sender), "Insufficient balance");
    _burn(msg.sender, amount);
    emit Redeem(msg.sender, amount);
}
```
## Deployment

The contract is deployed with an initial supply of 1,000,000 tokens to the contract deployer.

## License

This project is licensed under the terms of the MIT license. 

```javascript
This README.md provides an overview of the DegenToken smart contract, its features, usage instructions, deployment details, and licensing information.
````

## Author

Richard Pelarios BSIT
@Chard-web


