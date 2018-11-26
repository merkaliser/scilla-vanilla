# REFUNDABLE CROWDSALE CONTRACT
Refundable Crowd Sale contract allows the owner of a token doing crowdsale to change the state of sale depending if the goal has been achieved or not.If the goal is not achieved in a given time then he can change the state of sale to refunding and all the buyers/investors to initiate a refund of their investments. If the goal is achieved before a given time limit then the owner can change state of sale to closed and can withdraw the zil raised .

## TEST CASES

1.deposit : a user `[_sender]`: `0x0DF797A389C75520B9FBDC2F7AE2266B994776AF` send zil coins to a contract to buy tokens .Expected `[SUCCESS]` 
2.deposit : a user `[_sender]`: `0x1648634E0ECAA48C36A5C137FFB1830389DDF4AA` send zil coins to a contract to buy tokens .Expected `[SUCCESS]` 
3.deposit : a user `[_sender]`: `0x1EB825DC86C189B8E693013CB9CFFA77C9AD1134` send zil coins to a contract to buy tokens .Expected `[SUCCESS]`  
4.closed : `payee` (owner of tokens/contract) tries to change the state from `active` to `closed` .Expected `[FAILURE]` 
5.beneficiaryWithdraw : a user `[_sender]`: `0x1648634E0ECAA48C36A5C137FFB1830389DDF4AA` send a request to withdraw his/her zil coins .Expected `[FAILURE]` `state` is not `refunding`
6.withdrawPrimary : `payee` (owner of tokens/contract) send a request to withdraw his/her zil coins .Expected `[FAILURE]` `state` is not `closed`
7.deposit : a user `[_sender]`: `0x2624AE774221A5C7DF329535B40C60E2BD85BD2A` send zil coins to a contract to buy tokens .Expected `[SUCCESS]`
8.deposit : a user `[_sender]`: `0x355677AA606A408939A717A1ED1F66931377FEFF` send zil coins to a contract to buy tokens .Expected `[SUCCESS]`
9.refunding : `payee` (owner of tokens/contract) tries to change the state from `active` to `refunding` .Expected `[FAILURE]` as goal already achieved 
10.closed : `payee` (owner of tokens/contract) tries to change the state from `active` to `closed` .Expected `[SUCCESS]` 
11.withdrawPrimary : `payee` (owner of tokens/contract) send a request to withdraw his/her zil coins .Expected `[SUCCESS]` 


