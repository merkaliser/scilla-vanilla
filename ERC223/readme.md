# ERC223 Token Contract 

ERC223 Token Standard is more advanced version of Fungible Token contract which provides more secure and safer methods to transfer tokens to an address.

# Test Case
1. balanceOf : balanceof the token owner .Expected `[SUCCESS]`
2. totalSupply : total supply of tokens at present. Expected: [Success] `10000`
3. transfer : transfer tokens from `_sender` to `to` .Expected `[SUCCESS]` `value:500`.
4. transfer : transfer tokens from `_sender` to `to` .Expected `[Insufficient balance]` `value:9600`.
5. approve :`_sender` approves the/gives permission to the spender to transfer tokens on behalf of token owner. Expected: [Success] `value`: `500` .
6. approve :`_sender` approves the/gives permission to the spender to transfer tokens on behalf of token owner. Expected: [Success] `value`:`1000` .
7. transferFrom : spender transfer tokens from token owner `from` to token owner `to`.Expected : `[SUCCESS]`. `value`:`400`.
8. transferFrom : spender transfer tokens from token owner `from` to token owner `to`.Expected : `[Tokens to transfer cannot be greater than available or authorized value]`. `value`:`2000`.
9. allowance : number of tokens allowed by token `owner` to  `spender`.Expected :`[SUCCESS]`.
10. safeApprove : updates the number of tokens allowed to spender. If `currentValue` equals to tokens allowed to spender , updates allowed tokens with `Value`.Expected : `[Spender Approved]` , `caurrentValue`:`100`,`Value`:`800`.

11. burn : Burns given tokens from `_sender` and `tokenSupply` if balance of `_sender` >= `value`. Expected:`[Burned]` ,`value`:`300`.
12. burn : Burns given tokens from `_sender` and `tokenSupply` if balance of `_sender` >= `value`. Expected:`[Insufficient balance cannot burn]` ,`value`:`3000`.

13. burnFrom : Burns tokens from `_sender`(spender),allowed to spender and tokenSupply if balance of `_sender` >= `value` and `value` <= tokens allowed to `spender`.Expected:`[Insufficient balance cannot burn]` `value`:`3000`.
14. burnFrom : Burns tokens from `_sender`(spender),allowed to spender and tokenSupply if balance of `_sender` >= `value` and `value` <= tokens allowed to `spender`.Expected:`[Insufficient balance cannot burn]` `value`:`500`.

## List of transitions to be added

  * a transition to distinguish between sending tokens to an address of a user and a contract.
  * events and interfaces 

## RESULT

  * `_totalSupply` : 9200
  
  ### balances
  * 0x23271327E72F96AAB882F614B467EBB5ED3003D9 : 600
  * 0x1b5928d9e0f0667d106267f61de4c6e8312b3aef : 8600
  
  ### allowed
  *  0xf83c97044c0b5c8dc38cf5a57c23e03c396aeeff : 800    
  *  0xfc951123d89d0148e8f65c5842afe081dc1646d1 : 500