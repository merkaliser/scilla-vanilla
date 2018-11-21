## Faucet Contract
It contains Faucet Contract implementation in Scilla.

References taken:<br>
https://github.com/WeTrustPlatform/erc20faucet-contracts/blob/master/contracts/ERC20Faucet.sol
## Test cases

0. add: adds the pausable address with specified role `True`. Expected: [Success].
1. renounce: updates the pausable address with specified role `False`. Expected: [Success] .
2. remove: removes the pausable address with specified role . Expected: [Success] 
3. has: checks if the pausable address exists with specified role. Expected: [Success] `False`. 
4. has: checks if the pausable address exists with specified role. Expected: [Success] `True`
5. renounce: here it updates the pausable address with specified role `False`. Expected: [Success].

