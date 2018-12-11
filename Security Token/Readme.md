# Security Token Contract

It contains Security Token Contract (ERC 1400) implementation in Scilla.
It contains the functions required for Security token implementation.

References taken:<br>
https://github.com/ethereum/EIPs/issues/1400 <br>
https://github.com/ethereum/EIPs/issues/1411<br>

## Rationale

Being able to associate metadata with individual fungible tokens is useful when building functionality associated with those tokens.

For example, knowing when an individual token was minted allows vesting or lockup logic to be implemented for a portion of a token holders balance.

Tokens that represent securities often require metadata to be attached to individual tokens, such as the category of share or restrictions associated with the share.

Being able to associate arbitrary metadata with groups of tokens held by users is useful in a variety of use-cases. It can be used for token provenance (i.e. recording the previous owner(s) of tokens) or to attach data to a token which is then used to determine any transfer restrictions of that token.

In general it may be that whilst tokens are fungible under some circumstances, they are not under others (for example in-game credits and deposited balances). Being able to define such groupings and operate on them whilst maintaining data about the overall distribution of a token irrespective of this is useful in modelling these types of assets.

A Partially-Fungible Token allows for attaching metadata to a partial balance of a token holder. These partial balances are called tranches and are indexed by a bytes32 \_tranche key which can be associated with metadata on-chain or off-chain.

The specification for this metadata, beyond the existence of the \_tranche key to identify it, does not form part of this standard. The token holders address can be paired with the tranche to use as a metadata key if data varies across token holders with the same tranche (e.g. a "restricted" tranche may be associated with different lock up dates for each token holder).

For an individual owner, each token in a tranche therefore shares common metadata.

Token fungibility includes metadata so we have:

for a specific user, tokens within a given tranche are fungible
for a specific user, tokens from different tranches may not be fungible

Tokens are operated upon at a tranche granularity, but data about the overall supply of tokens and overall balances of owners is also tracked.

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
