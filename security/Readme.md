# ERC777 Token Contract
It contains ERC777 Token Contract implementation in Scilla.
It contains the functions required for ERC777 token implementation.

References taken:<br>
https://github.com/ethereum/EIPs/blob/master/EIPS/eip-777.md
https://github.com/jacquesd/ERC777/blob/master/contracts/examples/ReferenceToken.sol


## Test cases

1. name: name of the token. Expected: [Success] `ERC777`.
2. symbol: symbol of the token. Expected: [Success] `Merkalise`.
3. granularity: granularity of the token i.e. multiple of that can only be sent, for granularity=4, no. of tokens that can be sent are  as 4,8 etc. Expected: [Success] `4` 
4. totalSupply: total supply of tokens at present. Expected: [Success] `1000`
5. authorizeOperator: `_sender` authorizes the `operator` to use his all tokens. Expected: [Success]. 
6. isOperatorFor: checks for if `operator` is present for particular `tokenHolder`. Expected: [Success] `Operator found`.
7. Send: Sends the given `amount` of tokens from `_sender` to `to`. Expected: [Success].
8. operatorSend: Sends the given `amount` of tokens from `from` to `to`. Expected: [Success].
9. Burn: Burns the given `amount` of tokens of the `_sender`. Expected: [Success].
10. operatorBurn: Burns the given `amount` of tokens of `from`. Expected: [Success].
11. revokeOperator: Revokes the `operator` of the `_sender`. Expected: [Success].
12. operatorSend: if operator is not authorized. Expected: `Transfer not allowed`.
13. operatorBurn: if operator is not authorized. Expected: `Transfer not allowed`. 
14. isOperatorFor: if operator is not present for `tokenHolder`. Expected: `Operator found failed`.
15. Send: if `_sender` tries to send more `amount` of tokens than his balance. Expected: `Transferred: 0`.
16. Send: if `_sender` tries to send non granular `amount` of tokens. Expected: `Not granular`.
17. Burn: if `_sender` tries to burn more `amount` of tokens than his balance. Expected: `Balance insuffucient`.
18. Burn: if `_sender` tries to burn non granular `amount` of tokens. Expected: `Not granular`.

Similiar tests exists for `operatorSend` and `operatorBurn` for testCases 15,16,17,18 respectively.
