## System spec

OS: MacOS High Sierra

Go version: go1.12.1 darwin/amd64

## Fork gaia v2.0.0 repository

https://github.com/cosmos/gaia/tree/v2.0.0

## Clone the repository in local machine

```
$ git clone https://github.com/kogisin/gaia/tree/v2.0.0
```

## Get gaia-13006 testnet genesis.json

```
$ curl https://raw.githubusercontent.com/cosmos/testnets/master/gaia-13k/genesis.json > $HOME/.gaiad/config/genesis.json
```

## Import wallet 

I used this wallet throughout the previous testnets. 

I verified the below account is included in the genesis file

```
$ gaiacli keys add <name> --recover
```

Address: `cosmos1x5wgh6vwye60wv3dtshs9dmqggwfx2ldnqvev0`

## Create gentx

```
$ sudo gaiad gentx \
--name=JayB \
--amount=500muon \
--min-self-delegation=1 \
--node-id=$(sudo gaiad tendermint show-node-id) \
--pubkey=$(sudo gaiad tendermint show-validator)
```


## UnmarshalJSON Error 

```
ERROR: UnmarshalJSON cannot decode empty bytes
```


