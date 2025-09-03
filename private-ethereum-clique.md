# How to setup raspberry pi 5 running private ethereum PoA (Clique) Consensus 

## 0. Prepare project directory
```sh
mkdir ethereum-private
cd ethereum-private
mkdir node1 node2
touch info.txt
--- open vcode
code .
```

## 1. Making account on folder node1 and node2
```sh
geth --datadir "./data" account new
--- open info.txt add public address and password information
```
## 2. Make file privateblock.json as GENESIS BLOCK
```json
{
  "config": {
    "chainId": 1234567,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0,
    "istanbulBlock": 0,
    "berlinBlock": 0,
    "clique": {
      "period": 5,
      "epoch": 30000
    }
  },
  "difficulty": "1",
  "gasLimit": "8000000",
  "extradata": "0x0000000000000000000000000000000000000000000000000000000000000000{ INITIAL_SIGNER_ADDRESS }0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  "alloc": {
    "{ FIRST_NODE_ADDRESS }": {
      "balance": "3000000000000000000000000000000000000"
    },
    "{ SECOND_NODE_ADDRESS }": {
      "balance": "3000000000000000000000000000000000000"
    }
  }
}

```
