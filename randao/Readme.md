# RANDAO Contract
It contains RANDAO Contract implementation in Scilla.

References taken:<br>
https://github.com/randao/randao/blob/master/contracts/Randao.sol

## Test cases

1. shaCommit: get the sha256 hash of `secret`. Expected: [Success] `0x9b65b044264bd07cae9001dfe2c7b240b7bfcf39b4ce111d5e178bd7e9412a88`.
2. commit: `commitment` (i.e. the sha256 hash of any number) is provided in between the commit phase (`5` to `15`) with correct `_deposit` (`_amount`). Expected: [Success] `successful`.
3. commit: wrong `_amount` of zils i.e. required `deposit` is not sent. Expected: [Failure] `deposit amount of zil is not equal to deposit required`.
4. getCommitment: `_sender` can see the `commitment` he has made. Expected: [Success] `0x9b65b044264bd07cae9001dfe2c7b240b7bfcf39b4ce111d5e178bd7e9412a88`.
5. getCommitment: for no `commitment` by `sender`. Expected: [Failure] `commitment not found for _sender`. 
(2 more successful commits are done in the commit phase by 2 more accounts so that now we have 3 accounts participating in contract.)
6. commit: trying to commit after the `commit` phase ends (after `15`). Expected: [Failure] `Failed, deadline finished to commit` 
7. reveal: In the reveal phase (`16` to `20`), one has to reveal the secret (number) whose `commitment` was submitted in commit phase(`5` to `15`) . Expected: [Success] `successful`.
8. reveal: if the secret submitted doesnot match with the sha256 `commitment`. Expected: [Failure] `Failed, wrong secret revealed`.
9. reveal: Reveal the secret (number) at `20` whose `commitment` was submitted in commit phase. Expected: [Success] `successful`.
10. reveal: try to reveal the secret after the reveal phase is over. Expected: [Failure] `Failed, deadline finished to reveal`.
Hence, 2 out of 3 `commitments` have revealed secret in reveal phase.
11. getRandom: After the reveal phase is over (after `20`), one can get the random number generated. Expected: [Success]`606`.
12. getMyBounty: After the reveal phase is over (after `20`), one can get his share of bounty. Expected: [Success] `successful`.`60` => `50` (bounty divide share) + `5` (deposit) + `5` (fine as 1 commit didnot successfully reveal).
13. getMyBounty: try to get bounty when secret was not revealed in reveal phase. Expected: [Failure] `Failure, didnot reveal in deadline`.
14. getMyBounty: try to get bounty when it didnot `commit` in commit phase . Expected: [Failure]`Failure, didnot commit`. 
15. getMyBounty: try to get bounty before the reveal phase is over. Expected: [Failure] `Failure, reveal phase has not ended yet`.
16. commit: try to `commit` before commit phase (`5` to `15`)has started. Expected: [Failure] `Failed, early to commit`.
17. reveal: try to `reveal` before reveal phase (`15`) has started. Expected: [Failure] `Failed, early to reveal`.

