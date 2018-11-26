# RANDAO Contract
It contains RANDAO Contract implementation in Scilla.

References taken:<br>
https://github.com/randao/randao/blob/master/contracts/Randao.sol


## Randao in Scilla
First of all, we need to create a RANDAO contract in the blockchain,
which defines the participation rules.
Then the basic process of generating a random number can be divided into
three phases:

### The first phase (commit phase): collecting valid sha3(s)
Anyone who want to participate in the random number generation needs to
send a transaction to the contract with required deposit as pledge in a specified
time period, accompanied by the result of sha3(s), s is the secret number respective picked by
participant.

### The second phase (reveal phase): collecting valid secrets
After the first phase, anyone who submitted sha3(s) successfully needs
to send a transaction with the secret number s in the first stage to
contract within a specified time period. Contract will check if s is
valid by running sha3 against s and comparing the result with previous
committed data. Valid s will be saved to the collection of seeds to finally
generate the random number by concatenating individual secrets.How to use this number to further generate random number using this number as a seed can be done by contracts requesting for random number.

### The third phase: calculating a random number, refund deposits, fines and bonus
1. After phase 2 is complete, random number is generated that can be sent to all other contracts that requested the random number before.
2. Contract will send back the deposit to the participants who successfully took part in both phases, and the profit (fine + consumer's bounty) is divided into equal parts and sent to all participants as an additional bonus. 
3. Participants failing to reveal the secret number s cannot get refund their deposits and this amount is used as a fine.


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

