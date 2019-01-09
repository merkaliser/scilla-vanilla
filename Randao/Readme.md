# RANDAO Contract
It contains RANDAO Contract implementation in Scilla.

References taken:<br>
https://github.com/randao/randao/blob/master/contracts/Randao.sol

Past stable versions :
1. https://github.com/merkaliser/scilla-vanilla/tree/5d19d87e0286d57c87ef4872642cfdb0717fc6cc/randao
2. https://github.com/merkaliser/scilla-vanilla/tree/d6147e5c51cf365379152a6d823fe87e4b5c0080/Randao [Resettable single Contract]

## Randao in Scilla
First of all, we need to create a RANDAO contract in the blockchain,
which defines the participation rules.
Then the basic process of generating a random number can be divided into
three phases:

##### Add Compaign
Set the compaign using `setCompaign`. Parallel Compaigns can run through. CompaignID should be any unique number.

##### The first phase (commit phase): collecting valid sha3(s)
Anyone who want to participate in the random number generation needs to
send a transaction to the contract with required deposit as pledge in a specified
time period, accompanied by the result of sha3(s), s is the secret number respective picked by
participant. `commit` is used with sha256 hash of any number as parameter. It cannot be equal to equivalent to secret 0.

##### The second phase (reveal phase): collecting valid s
After the first phase, anyone who submitted sha3(s) successfully needs
to send a transaction with the secret number s in the first stage to
contract within a specified time period. Contract will check if s is
valid by running sha3 against s and comparing the result with previous
committed data. Valid s will be saved to the collection of seeds to finally
generate the random number. `reveal` is used with secret as parameter.

In case of failure of condition of minimum participants, `reveal` can be used by participant or founder to get back their deposit/ bounty respectively.


##### The third phase: calculating a random number, refund deposits, fines and bonus
1. After phase 2 is complete, random number is generated that can be sent to all other contracts that requested the random number before. `getRandom` returns Random number.
2. Contract will send back the deposit to the participants who successfully took part in both phases, and the profit (fine + consumer's bounty) is divided into equal parts and sent to all participants as an additional bonus. `getMyBounty` provides bounty.
3. Participants failing to reveal the secret number s cannot get refund their deposits and this amount is used as a fine.
4. Random no is calculated by `[dist(sha256hash( [dist(sha256hash( [dist(0,h1)/s1] ),h2) /s2 ]),h3)/s3] and so on.....`

## Rationale

The contract is deployed by the one who wants to generate random number (founder/consumer). Following fields are required for compaign :
  * **deposit** : deposit required (zils) by participants to take part in phase 1. This can be thought as security deposit for generating the random no. After both phases are successfully completed, deposits are returned alongwith bounty.
  * **commitBalkline** : Initial (BlockNumber) when phase 1 will start. Before this no one can take part.
  * **commitDeadline** : Deadline (BlockNumber) when phase 1 ends. After phase 1 ends no more participants can take part.
  * **bnum** : Deadline (BlockNumber) when phase 2 ends. After phase 2 ends, random no. is generated. In between commitDeadline and bnum is the phase 2.
  * **_amount** : zils provided by founder as reward (`_bounty`) to be distributed equally amongst participants when both phases are finished. This should be equal to contract _balances in that state. 
  * **minParticipant** : minimum no of participants that are required to take part in phase 1. If the no of participants that took part in phase 1 are less than this i.e. if it fails to collect enough sha3(s) within the time period, then deposits are returned in phase 2 by reveal function itself.
  * **compaignID** : unique identification no. for running compaign.

Following test cases are explained in sequence of how transitions can be called.

## Test cases

1. setCompaign : Set compaign deposit of bounty by consumer by sending `_amount`. Expected: [Success]. Event: `Compaign Created`.
2. commit: `commitment` (i.e. the sha256 hash of any number) is provided in between the commit phase (`5` to `15`) with correct `_deposit` (`_amount`). Expected: [Success]. Event: `LogCommit`. Note, 3 successful commits are already present in that state.
3. commit: `commitment` cannot be submitted twice by any address. Expected: [Failure] `-13`.
4. commit: wrong `_amount` of zils i.e. required `deposit` is not sent. Expected: [Failure]`-1`.
5. getCommitment: `_sender` can see the `commitment` he has made. Expected: [Success] `0x9b65b044264bd07cae9001dfe2c7b240b7bfcf39b4ce111d5e178bd7e9412a88`. Event: `Commitment`.
6. getCommitment: for no `commitment` by `sender`. Expected: [Failure]`-5`. 
7. commit: trying to commit after the `commit` phase ends (after `15`). Expected: [Failure] `-2`. 
8. reveal: In the reveal phase (`16` to `20`), one has to reveal the secret (number) whose `commitment` was submitted in commit phase(`5` to `15`) . Expected: [Success]. Event: `LogReveal`.
9. reveal: if the secret submitted doesnot match with the sha256 `commitment`. Expected: [Failure] `-9`.
10. reveal: Reveal the secret (number) at `20` (as 20 bnum is included in 16 to 20 range) whose `commitment` was submitted in commit phase. Expected: [Success].
11. reveal: try to reveal the secret after the reveal phase is over. Expected: [Failure] `-6`.
12. getRandom: After the reveal phase is over (after `20`), consumer can get the random number generated. Expected: [Success]`1687564546916791024936105827028501796611780502564660906526728574680759`. Event: `RandomNumber`.
13. getMyBounty: After the reveal phase is over (after `20`), one can get his share of bounty. Expected: [Success] `successful`.`43` => `33` (bounty divide share) + `5` (deposit) + `5` (fine as 1 commit didnot successfully reveal). Event: `Commitment`.
14. getMyBounty: try to get bounty when secret was not revealed in reveal phase. Expected: [Failure] `-4`.
15. getMyBounty: try to get bounty when it didnot `commit` in commit phase . Expected: [Failure] `-5`. 
16. getMyBounty: try to get bounty before the reveal phase is over. Expected: [Failure] `-4`.
17. commit: try to `commit` before commit phase (`5` to `15`)has started. Expected: [Failure] `-2`.
18. reveal: try to `reveal` before reveal phase (`15`) has started. Expected: [Failure] `-6`.
19. reveal: try to `reveal` if commits in phase1 are less than required minimum participants. `_deposit` is refunded to participants of phase 1. Random no. generation fails. Expected:  `Failed compaign and refunded deposit as minParticipants < total commits`. `deposit` is tranferred.
20. setCompaign : no 2 compaignIDs can be same . Expected: [Failure] `-12`.
21. getRandom : non consumer cant get the random number. Expected: [Failure] `-11`.
22. reveal : to get back the bounty of consumer/ founder in case if commits in phase1 are less than required minimum participants. Expected:  `Failed compaign and refunded deposit as minParticipants < total commits`. `bounty is transferred`.
