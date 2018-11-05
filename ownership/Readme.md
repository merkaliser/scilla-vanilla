# Ownership Contract
It contains Ownership Contract implementation in Scilla.

References taken:<br>
https://github.com/OpenZeppelin/openzeppelin-solidity/tree/master/contracts/ownership


## Test cases

0. Is owner: Expected: `true`.
1. Transfer Ownership: Ownership is not transferred by non owner. Expected: `not an owner`
2. Transfer Ownership: Ownership is transferred by owner. Expected: `transfer successful` 
3. Renounce Ownership: Renouncing ownership is not allowed by non owner. Expected: `not an owner`
4. Renounce Ownership: Renouncing ownership is successful by owner. Expected: `Renounce Ownership successful` 
5. Is owner: Expected: `false` 

