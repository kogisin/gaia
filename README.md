## System spec

OS: MacOS High Sierra

Go version: go1.12.1 darwin/amd64

## Fork gaia v2.0.0 repository

https://github.com/cosmos/gaia/tree/v2.0.0

## Clone the repository in local machine

```
$ git clone https://github.com/kogisin/gaia/tree/v2.0.0
```

## Create or import wallet 

Make sure your created wallet is included in `accounts` field in `genesis.json` file and have some tokens.
I verified my imported account is included in the `genesis.json` file

Address: `cosmos1x5wgh6vwye60wv3dtshs9dmqggwfx2ldnqvev0`

```
Create wallet
$ gaiacli keys add <name>

Import wallet
$ gaiacli keys add <name> --recover

Include your account in genesis.json file
$ gaiad add-genesis-account validator 100000000000000000muon
```

## Execute the gentx command providing below set of inputs

```
$ sudo gaiad gentx \
--name=JayB \
--amount=500muon \
--min-self-delegation=1 \
--node-id=$(sudo gaiad tendermint show-node-id) \
--pubkey=$(sudo gaiad tendermint show-validator)
```


## #1. Error: ERROR: UnmarshalJSON cannot decode empty bytes 

Problem with gaia-13006 testnet genesis.json is that `gentxs` field in `app_state` object is `null`.

```
$ curl https://raw.githubusercontent.com/cosmos/testnets/master/gaia-13k/genesis.json > $HOME/.gaiad/config/genesis.json
```

If it is null, then it returns the following error

```
ERROR: UnmarshalJSON cannot decode empty bytes 
```
 


