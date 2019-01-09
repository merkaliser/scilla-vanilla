## Faucet Contract
It contains Faucet Contract implementation in Scilla.

References taken:<br>
https://github.com/WeTrustPlatform/erc20faucet-contracts/blob/master/contracts/ERC20Faucet.sol


## Test cases

1. getTokens: get the tokens by `_amount`. Expected: [Success] `5`.
2. setMaxAllowance: sets maximum allowance of tokens to claim (allowed to owner only). Expected: [Success] `500`.
3. reclaimTokens: reclaim the tokens (allowed to owner only). Expected: [Success] `true`.
4. setPause: pauses the selling of tokens  Expected: [Success] Event:`Paused`. 
5. BalanceOf: returns balance of `tokenOwner`. Expected: [Success] `10`
6. MaxAllowance:The maximum amount (inclusive) allowed to claim. Expected: [Success] `500`.
7. Transfer: transfers tokens from `_sender` to `to`. Expected: [Success] Event:`Transfer`.
8. TransferFrom: transfers tokens from `from` to `to`. Expected: [Success] Event:`TransferFrom`.
9. Approve: approves `tokens` to `spender` by `_sender`. Expected: [Success] Event:`Approve`.
10. Allowance: checks whether `tokenOwner` has approved `spender`. Expected: [Success] Event:`Allowance`. 

