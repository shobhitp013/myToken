# myToken
Solidity is the programming language used to create smart contracts on the Ethereum blockchain. These contracts are self-executing programs that manage and automate the transfer of digital assets like your MyToken
# Desciption 
this code provides a basic structure for a MyToken contract. It defines key details like the token's name, symbol, and total supply. It also includes a placeholder transfer function for transferring tokens between accounts.
# Getting Started
# Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., mytoken.sol). Copy and paste the following code into the file:

// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/


contract MyToken {
    string public tokenName = "CRAFT";
    string public tokenAbbvr = "CFT";
    uint public totalSupply = 0;
    
    mapping(address => uint) public balances;
    
    function mint(address _to, uint _value) public {
        require(_to != address(0), "_to cannot be the zero address");
        
        totalSupply += _value;
        balances[_to] += _value;
    }
    
    function burn(address _from, uint _value) public {
        require(balances[_from] >= _value, "Insufficient balance");
        
        balances[_from] -= _value;
        totalSupply -= _value;
    }
    
    function balanceOf(address _address) public view returns (uint256) {
        return balances[_address];
    }
}

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile mytoken.sol" button.
Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MY Token" contract from the dropdown menu, and then click on the "Deploy" button.
the transaction will availble.
# Authors
Shobhit Pandey
@shobhitp013
# License
This project is licensed under the MIT License - see the LICENSE.md file for details
