## Escrow Contract
It contains Escrow Contract implementation in Scilla.

References taken:<br>
https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/payment/escrow/Escrow.sol

## Test cases

0. primary: address of primary. Expected: [Success] `0x263c4ca003235af83c4f4bc065d00d4a67ffb617`.
1. transferPrimary: transfer primary. Expected: [Success] .
2. depositsOf: deposits of the any `payee` . Expected: [Success] 
3. deposit: deposit the `deposits` to `payee`. Expected: [Success] 
4. withdraw: withdraw the `deposits` from `payee`. Expected: [Success]. 
5. withdraw:  withdraw the `deposits` from `payee`. Expected: Failure as payee dont have so much deposits.
6. withdraw:  withdraw the `deposits` from `payee`. Expected: Failure as the withdrawee `_sender` is not primary. Error: `not primary`.
