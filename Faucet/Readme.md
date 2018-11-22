## Faucet Contract
It contains Faucet Contract implementation in Scilla.

References taken:<br>
https://github.com/WeTrustPlatform/erc20faucet-contracts/blob/master/contracts/ERC20Faucet.sol


## Test cases

0. getTokens: get the tokens by `_amount`. Expected: [Success].
1. setMaxAllowance: sets maximum allowance of tokens to claim (allowed to owner only). Expected: [Success] .
2. reclaimTokens: reclaim the tokens (allowed to owner only). Expected: [Success] 
3. setPause: pauses the selling of tokens  Expected: [Success]. 
4. BalanceOf: returns balance of `tokenOwner`. Expected: [Success] `True`
5. MaxAllowance:The maximum amount (inclusive) allowed to claim. Expected: [Success].
6. Transfer: transfers tokens from `_sender` to `to`. Expected: [Success].
7. TransferFrom: transfers tokens from `from` to `to`. Expected: [Success].
8. Approve: approves `tokens` to `spender` by `_sender`. Expected: [Success].
9. Allowance: checks whether `tokenOwner` has approved `spender`. Expected: [Success]. 

