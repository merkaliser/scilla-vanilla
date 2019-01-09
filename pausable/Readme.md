## Pausable Contract
It contains Pausable Contract implementation in Scilla.

References taken:<br>
https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/access/Roles.sol <br>
https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/access/roles/PauserRole.sol <br>
https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/lifecycle/Pausable.sol 

## Test cases

1. add: adds the pausable address with specified role `True`. Expected: [Success].
2. renounce: updates the pausable address with specified role `False`. Expected: [Success] .
3. remove: removes the pausable address with specified role . Expected: [Success].
4. has: checks if the pausable address exists with specified role. Expected: [Success] `False`.
5. has: checks if the pausable address exists with specified role. Expected: [Success] `True`.
6. renounce: here it updates the pausable address with specified role `False`. Expected: [Success].