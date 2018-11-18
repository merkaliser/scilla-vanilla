# Security Token Contract
It contains Security Token Contract (ERC 1400) implementation in Scilla.
It contains the functions required for Security token implementation.

References taken:<br>
https://github.com/ethereum/EIPs/issues/1400 <br>
https://github.com/ethereum/EIPs/issues/1411<br>


## Test cases

1. shaCommit: name of the token. Expected: [Success] `Security Token`.
2. commit: symbol of the token. Expected: [Success] `ST`.
3. commit: wrong deposit mints `_amount` of tokens of `tranche` specified. Expected: [Success] `deposit amount of zil is not equal to deposit required`.
4. getCommitment: total supply of tokens at present. Expected: [Success] `0x9b65b044264bd07cae9001dfe2c7b240b7bfcf39b4ce111d5e178bd7e9412a88`.
5. getCommitment: no sender of particular `tranche`. Expected: [Success] `commitment not found for _sender`. 
2 more successful commits done in phase1
6. commit: dead of the any `owner` . Expected: [Success] `Failed, deadline finished to commit` 
7. reveal: sends tokens by `tranche`. Expected: [Success] `successful`.

8. reveal:  Expected: [Success] `Failed, wrong secret revealed`.
at 19

9. reveal at 20

10. reveal: Expected: [Success] `Failed, deadline finished to reveal`.
so 2/3 revealed...
11. getRandom: revokes the given `operator` by `_sender`. Expected: [Success]`606`.
12. getMyBounty:60 => 50(bounty divide share)+5(deposit)+5(fine as 1 didnot successfully reveal) authorizes the given `operator` by `_sender` tranche. Expected: [Success] `authorized the operator for tranche`.
13. getMyBounty: sending the `tranche` balance by `operator`. Expected: [Success] `Failure, didnot reveal in deadline`.
14. getMyBounty: revokes the given `operator` by `_sender` tranche. Expected: [Success]`Failure, didnot commit`. 
15. getMyBounty: at 10 bnum if `operator` is present for `owner`. Expected: [Success] `Failure, reveal phase has not ended yet`.
16. commit: if `operator` is present for `owner` tranche. Expected: [Success] `Failed, early to commit`.
17. reveal: burns `amount` of tokens of `tranche`. Expected: [Success] `Failed, early to reveal`.

