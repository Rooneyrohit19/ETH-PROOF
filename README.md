# ETH-PROOF

## Step for Execution
**Execution Steps for GitHub README:**
To execute and deploy this contract, you can follow these general steps:

1. Install a development environment such as [Remix](https://remix.ethereum.org/).

2. Copy and paste the provided Solidity code into a new file with a `.sol` extension.

3. Compile the code using the Solidity compiler, ensuring that the version matches the one specified in the code, which is 0.8.22

4. Deploy the compiled smart contract.

5. To Interact you can mint, burn, and transfer tokens as defined in the contract.


## Explanation 
This Solidity code defines a basic ERC-20 compatible token contract named `MyTokenRO`. Let's go through the code step by step:

1. **SPDX License Identifier:**
   ```solidity
   // SPDX-License-Identifier: MIT
   ```
   This line indicates that the code is licensed under the MIT License.

2. **Solidity Version Declaration:**
   ```solidity
   pragma solidity =0.8.22;
   ```
   This line specifies the version of the Solidity compiler to be used (version 0.8.22 in this case).

3. **Contract Declaration:**
   ```solidity
   contract MyTokenRO {
   ```
   This declares the main contract named `MyTokenRO`.

4. **Public Variables:**
   ```solidity
   string public tokenName = "Rohit";
   string public tokenAbbr = "RO";
   uint public totalSupply = 0;
   ```
   These are public variables representing the token name, token abbreviation, and the total supply of the token, respectively.

5. **Mapping Variable:**
   ```solidity
   mapping(address => uint) public balances;
   ```
   This mapping is used to store the balances of each address holding the tokens.

6. **Mint Function:**
   ```solidity
   function mint(address _address, uint _value) public {
       totalSupply += _value;
       balances[_address] += _value;
   }
   ```
   The `mint` function is used to create new tokens. It increases the total supply and assigns the specified amount of tokens to the specified address.

7. **Burn Function:**
   ```solidity
   function burn(address _address, uint _value) public {
       if (balances[_address] >= _value) {
           totalSupply -= _value;
           balances[_address] -= _value;
       }
   }
   ```
   The `burn` function is used to destroy tokens. It checks if the address has enough tokens to burn and then decreases the total supply and the balance of the specified address.

8. **Transfer Function:**
   ```solidity
   function transfer(address _from, address _to, uint _value) public {
       require(balances[_from] >= _value, "Insufficient balance");
       balances[_from] -= _value;
       balances[_to] += _value;
   }
   ```
   This new `transfer` function allows transferring tokens from one address to another. It checks if the sender has enough tokens, and if so, it deducts tokens from the sender's balance and adds them to the recipient's balance.

