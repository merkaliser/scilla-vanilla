# Ownership Contract
It contains Ownership Contract implementation in Scilla.

References taken: <br>
https://github.com/OpenZeppelin/openzeppelin-solidity/tree/master/contracts/ownership

## Test cases

1. Is owner: Expected: `true`.
2. Transfer Ownership: Ownership is not transferred by non owner. Expected: `not an owner`.
3. Transfer Ownership: Ownership is transferred by owner. Expected: `transfer successful`.
4. Renounce Ownership: Renouncing ownership is not allowed by non owner. Expected: `not an owner`.
5. Renounce Ownership: Renouncing ownership is successful by owner. Expected: `Renounce Ownership successful`.
6. Is owner: Expected: `false`.