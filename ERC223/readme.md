# ERC223 Token Contract 

ERC223 Token Standard is more advanced version of Fungible Token contract which provides more secure and safer methods to transfer tokens to an address.

# Test Case
1.balanceOf : returns the balance of the address passed.
2.totalSupply : returns the total number of tokens in supply.
3.transfer : transfer tokens from `_sender` to `to` .
4.Approve : _sender gives permission to spender to transfer tokens.
5.transferFrom : spender transfer tokens from `from` to `to`.
6.Allowance : number of tokens allowed by token owner to  `spender`.
7.burn : subtract tokens from `_sender` and tokenSupply if balance of `_sender` >= `value`.
8.burnFrom : subtract tokens from `_sender`(spender),allowed to spender and tokenSupply if balance of `_sender` >= `value` and `value` <= tokens allowed to `spender`.

## List of transitions to be added

  * a transition to distinguish between sending tokens to an address of a user and a contract.
  * events and interfaces 
