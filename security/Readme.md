# Security Token Contract
It contains Security Token Contract (ERC 1400) implementation in Scilla.
It contains the functions required for Security token implementation.

References taken:<br>
https://github.com/ethereum/EIPs/issues/1400 <br>
https://github.com/ethereum/EIPs/issues/1411<br>


## Test cases

1. name: name of the token. Expected: [Success] `Security Token`.
2. symbol: symbol of the token. Expected: [Success] `ST`.
3. balanceOf: balance of the any `owner` . Expected: [Success] `1000` 
4. totalSupply: total supply of tokens at present. Expected: [Success] `1000`
5. balanceOfTranche: balance of particular `tranche`. Expected: [Success]. 
6. sendTranche: sends tokens by `tranche`. Expected: [Success].
7. defaultOperators: Expected: [Success].
8. defaultOperatorsTranche: Expected: [Success].
9. authorizeOperator: authorizes the given `operator` by `_sender`. Expected: [Success].
10. revokeOperator: revokes the given `operator` by `_sender`. Expected: [Success].
11. operatorSendTranche: sending the `tranche` balance by `operator`. Expected: [Success].
12. authorizeOperatorTranche: authorizes the given `operator` by `_sender` tranche. Expected: [Success].
13. revokeOperatorTranche: revokes the given `operator` by `_sender` tranche. Expected: [Success]. 
14. isOperatorFor: if `operator` is present for `owner`. Expected: [Success] .
15. isOperatorForTranche: if `operator` is present for `owner` tranche. Expected: [Success].
16. burn: burns `amount` of tokens of `tranche`. Expected: [Success].
17. mint: mints `amount` of tokens of `tranche`. Expected: [Success].





