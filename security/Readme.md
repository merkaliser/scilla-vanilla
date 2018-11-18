# Security Token Contract
It contains Security Token Contract (ERC 1400) implementation in Scilla.
It contains the functions required for Security token implementation.

References taken:<br>
https://github.com/ethereum/EIPs/issues/1400 <br>
https://github.com/ethereum/EIPs/issues/1411<br>


## Test cases

1. name: name of the token. Expected: [Success] `Security Token`.
2. symbol: symbol of the token. Expected: [Success] `ST`.
3. mint: mints `_amount` of tokens of `tranche` specified. Expected: [Success] `mint for tranche successful`.
4. totalSupply: total supply of tokens at present. Expected: [Success] `600`.
5. balanceOfTranche: balance of particular `tranche`. Expected: [Success] `600`. 
6. balanceOf: balance of the any `owner` . Expected: [Success] `600` 
7. sendTranche: sends tokens by `tranche`. Expected: [Success] `send tranche successful`.
8. defaultOperators: Expected: [Success] `0x263C4CA003235AF83C4F4BC065D00D4A67FFB617`.
9. defaultOperatorsTranche: Expected: [Success] `0x263C4CA003235AF83C4F4BC065D00D4A67FFB617`.
10. authorizeOperator: authorizes the given `operator` by `_sender`. Expected: [Success].
11. revokeOperator: revokes the given `operator` by `_sender`. Expected: [Success].
12. authorizeOperatorTranche: authorizes the given `operator` by `_sender` tranche. Expected: [Success] `authorized the operator for tranche`.
13. operatorSendTranche: sending the `tranche` balance by `operator`. Expected: [Success] `operator tranche send successful`.
14. revokeOperatorTranche: revokes the given `operator` by `_sender` tranche. Expected: [Success]. 
15. isOperatorFor: if `operator` is present for `owner`. Expected: [Success] `False (revoked)`.
16. isOperatorForTranche: if `operator` is present for `owner` tranche. Expected: [Success] `False (revoked)`.
17. burn: burns `amount` of tokens of `tranche`. Expected: [Success] `burn successful`.
18. sendTranche: tries to send tokens of `tranche` not present. Expected: [Failure] `[4]`.
19. burn : tries to burn `_amount` of tokens of `tranche` not present. Expected: [Failure] `burn unsuccessful`.
20. operatorSendTranche : sending the `tranche` balance by `operator` that is not present. Expected: [Failure] `not an operator`.
21. operatorSend : sending the `_amount` from `from` by `operator`. Expected: [Success] `operator send successful`.
22. operatorSend : trying to send the `_amount` by non `operator`. Expected: [Failure] `not an operator`.



