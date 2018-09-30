
### primary

```
{
    "_tag" : "primary",
    "_amount" : "0",
    "_sender" : "0x1234567890123456789012345678901234567890",
    "params" : [
       
    ]
}
```


### transferPrimary

```
{
    "_tag" : "transferPrimary",
    "_amount" : "0",
    "_sender" : "0x1234567890123456789012345678901234567890",
    "params" : [
        {
            "vname": "recipient",
            "type" : "ByStr20",
            "value" : "0x12345678901234567890123456789012345678cd"
        }
    ]
}
```


### depositsOf

```
{
    "_tag" : "depositsOf",
    "_amount" : "0",
    "_sender" : "0x12345678901234567890123456789012345678cd",
    "params" : [
        {
            "vname": "payee",
            "type" : "ByStr20",
            "value" : "0x1234567890123456789012345678901234567890"
        }
    ]
}
```


### deposit

```
{
    "_tag" : "deposit",
    "_amount" : "0",
    "_sender" : "0x1234567890123456789012345678901234567890",
    "params" : [
        {
            "vname": "payee",
            "type" : "ByStr20",
            "value" : "0x12345678901234567890123456789012345678cd"
        },
          {
            "vname": "deposits",
            "type" : "Uint128",
            "value" : "10"
        }
    ]
}
```


### withdraw

```
{
    "_tag" : "withdraw",
    "_amount" : "0",
    "_sender" : "0x12345678901234567890123456789012345678cd",
    "params" : [
       {
            "vname": "payee",
            "type" : "ByStr20",
            "value" : "0x1234567890123456789012345678901234567890"
        },
          {
            "vname": "deposits",
            "type" : "Uint128",
            "value" : "1"
        }
    ]
}
```


