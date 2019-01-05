## Faucet Contract
It contains Faucet Contract implementation in Scilla.

References taken:<br>
https://github.com/WeTrustPlatform/erc20faucet-contracts/blob/master/contracts/ERC20Faucet.sol


## Test cases

0. getTokens: get the tokens by `_amount`. Expected: [Success] `5`.
1. setMaxAllowance: sets maximum allowance of tokens to claim (allowed to owner only). Expected: [Success] `500`.
2. reclaimTokens: reclaim the tokens (allowed to owner only). Expected: [Success] `true`.
3. setPause: pauses the selling of tokens  Expected: [Success] Event:`Paused`. 
4. BalanceOf: returns balance of `tokenOwner`. Expected: [Success] `10`
5. MaxAllowance:The maximum amount (inclusive) allowed to claim. Expected: [Success] `500`.
6. Transfer: transfers tokens from `_sender` to `to`. Expected: [Success] Event:`Transfer`.
7. TransferFrom: transfers tokens from `from` to `to`. Expected: [Success] Event:`TransferFrom`.
8. Approve: approves `tokens` to `spender` by `_sender`. Expected: [Success] Event:`Approve`.
9. Allowance: checks whether `tokenOwner` has approved `spender`. Expected: [Success] Event:`Allowance`. 

