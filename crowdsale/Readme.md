# CrowdSale Contract
It contains CrowdSale Contract implementation in Scilla.
It contains the functions required for CrowdSale implementation.

References taken:<br>
https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/crowdsale/Crowdsale.sol


## Test cases

1. wallet: address of the wallet for collecting zils. Expected: [Success] `0x6d8794a2b6b98eabc1f466d0c5a4c1ee9e0f77f4`.
2. rate: rate of the token. Expected: [Success] `5`.
3. tokensRaised: number of tokens raised till now. Expected: [Success] `0` 
4. buyTokens: `_sender` buys from `10` zils for `beneficiary`. Expected: [Success]
5. buyTokens: `_sender` tries to buy from `9` zils for `beneficiary` that is not a rate `5` multiple. Expected: `Code - 5` . 
6. buyTokens: `_sender` is `beneficiary` and adds `20` zils. Expected: [Success].

