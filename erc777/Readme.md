# ERC777 Token Contract
It contains ERC777 Token Contract implementation in Scilla.
It contains the functions required for ERC777 token implementation.

References taken:<br>
https://github.com/ethereum/EIPs/blob/master/EIPS/eip-777.md
https://github.com/jacquesd/ERC777/blob/master/contracts/examples/ReferenceToken.sol


## Test cases

1. name: name of the token. Expected: [SUCCESS] `ERC777`.
2. symbol: symbol of the token. Expected: [SUCCESS] `Merkalise`.
3. granularity: granularity of the token i.e. multiple of that can only be sent, for granularity=4, no. of tokens that can be sent are  as 4,8 etc. Expected: [SUCCESS] `4` 
4. totalSupply: total supply of tokens at present. Expected: [SUCCESS] `1000`
5. authorizeOperator: `_sender` authorizes the `operator` to use his all tokens. Expected: [SUCCESS]. 
6. isOperatorFor: checks for if `operator` is present for particular `tokenHolder`. Expected: [SUCCESS] `Operator found`.
7. Send: Sends the given `amount` of tokens from `_sender` to `to`. Expected: [SUCCESS].
8. operatorSend: Sends the given `amount` of tokens from `from` to `to`. Expected: [SUCCESS].
9. Burn: Burns the given `amount` of tokens of the `_sender`. Expected: [SUCCESS].
10. operatorBurn: Burns the given `amount` of tokens of `from`. Expected: [SUCCESS].
11. revokeOperator: Revokes the `operator` of the `_sender`. Expected: [SUCCESS].
