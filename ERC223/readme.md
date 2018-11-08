# ERC223 Token Contract 

ERC223 Token Standard is more advanced version of Fungible Token contract which provides more secure and safer methods to transfer tokens to an address.

## Test Cases
1.balanceOf : balanceof the token owner .Expected `[SUCCESS]` <br/>
2.totalSupply : total supply of tokens at present. Expected: `[Success]` `10000` <br/>
3.transfer : transfer tokens from `_sender` to `to` .Expected `[SUCCESS]` `value:500`. <br/>
4.transfer : transfer tokens from `_sender` to `to` .Expected `[Insufficient balance]` `value:9600`. <br/>
5.approve :`_sender` approves the/gives permission to the spender to transfer tokens on behalf of token owner. Expected: <br>                        `[Success]` `value`: `500` . <br/>
6.approve :`_sender` approves the/gives permission to the spender to transfer tokens on behalf of token owner. Expected: <br>                        `[Success]`, `value`:`1000` . <br/>
7.transferFrom : spender transfer tokens from token owner `from` to token owner `to`.Expected : `[SUCCESS]`. `value`:`400`. <br/>
8.transferFrom : spender transfer tokens from token owner `from` to token owner `to`.Expected : <br>
 															`[Tokens to transfer cannot be greater than available or authorized value]`. `value`:`2000`. <br/>
9.allowance : number of tokens allowed by token `owner` to  `spender`.Expected :`[SUCCESS]`. <br/>
10.safeApprove : updates the number of tokens allowed to spender. If `currentValue` equals to tokens allowed to spender , updates <br>                     allowed tokens with `Value`.Expected : `[Spender Approved]` , `caurrentValue`:`100`,`Value`:`800`. <br/>
11.burn : Burns given tokens from `_sender` and `tokenSupply` if balance of `_sender` >= `value`. Expected:`[Burned]` ,`value`:`300`. <br/>
12.burn : Burns given tokens from `_sender` and `tokenSupply` if balance of `_sender` >= `value`. Expected: <br>                                    `[Insufficient balance cannot  burn]` ,`value`:`3000`. <br/>
13.burnFrom : Burns tokens from `_sender`(spender),allowed to spender and tokenSupply if balance of `_sender` >= `value` and `value` <=                 tokens allowed to `spender`.Expected:`[Insufficient balance cannot burn]` `value`:`3000`. <br/>
14.burnFrom : Burns tokens from `_sender`(spender),allowed to spender and tokenSupply if balance of `_sender` >= `value` and `value` <=                 tokens allowed to `spender`.Expected:`[Insufficient balance cannot burn]` `value`:`500`. <br/>

## List of transitions to be added

  * a transition to distinguish between sending tokens to an address of a user and a contract.
  * events and interfaces 
