# How to Deploy Geth

## Build

make sure you're using go1.11.

`make geth`

cp build/bin/geth .

## Prerequisites

1. init coinbase account
`./geth --datadir eth1 account new`

2. allocate coin to the account which created in step 1
```json
{
    "config": {
        "chainId": 26632812188,
        "homesteadBlock": 0,
        "eip150Block": 0,
        "eip150Hash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "eip155Block": 0,
        "eip158Block": 0,
        "byzantiumBlock": 0,
        "constantinopleBlock": 0,
        "petersburgBlock": 0,
        "istanbulBlock": 0,
        "ethash": {}
    },
    "nonce": "0x0",
    "timestamp": "0x5ddf8f3e",
    "extraData": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "gasLimit": "0x47b760",
    "difficulty": "1",
    "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "coinbase": "0xdd5B4294F34684A2CD6C8EBE73FC1d0B32829F14",
    "alloc": {
        "0xdd5B4294F34684A2CD6C8EBE73FC1d0B32829F14": {
            "balance": "100000000000000000000"
        }
    },
    "number": "0x0",
    "gasUsed": "0x0",
    "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```

3. init blockchain
`./geth  --datadir eth1  init genesis.json`

4. create node
```bash
nohup ./geth --datadir "eth1" --networkid "49323217" --rpc --rpcapi "db,eth,net,web3,miner,personal" console >> 1.log 
```

5. attach js cli to node
`./geth attach http://127.0.0.1:8545`