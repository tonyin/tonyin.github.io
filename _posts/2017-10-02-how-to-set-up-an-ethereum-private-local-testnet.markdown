---
layout: post
title: 'HowTo: Set up an Ethereum private local testnet'
image: "/assets/img/2017/09/ETHEREUM-LOGO_LANDSCAPE_Black.png"
date: '2017-10-02 17:36:17'
tags:
- howto
- blockchain
- ethereum
- guides
- osx
- crypto
---

*Last Updated: 2 Oct 2017*

Ethereum is a decentralized blockchain platform for smart contracts. The protocol is designed in such a way that we can run Turing-complete (arbitrary length) applications. In this guide, we will go over how to set up our own private local testnet (Mac OS X). Questions, comments, and suggestions for improvements are always welcome.

### We need a private instance for testing

Anything published on the Ethereum public mainnet is immutable and consumes gas (Ether) to execute, which can be costly for testing purposes. Having our own Ethereum testnet allows us to test any smart contracts before we deploy it to either a public testnet or the public mainnet, which means we can catch as many errors as possible. It also happens to be a great learning experience.

### Guides already exist but are outdated or incomplete

From my research there are three guides that seem to be the most authoritative and useful on setting up a testnet, listed below in [#References](#references). If we combine together the three guides and a few of the StackExchange solutions, then we arrive at this guide.

<br />

---

# Table of Contents

- [Set up Mac OS X](#setupmacosx)
  - [Install geth](#installgethgoethereum)
  - [Sync with Ethereum mainnet (optional)](#syncwithethereummainnetoptional)
- [Create private blockchain](#createprivateblockchain)
  - [Create genesis config](#creategenesisblockconfiguration)
  - [Initialize genesis block](#initializethegenesisblock)
  - [Create new address and begin mining](#createanaddressandbeginmining)
  - [Check ETH balance](#checkethbalance)
- [Conclusion](#conclusion)
- [References](#references)

---

# Set up Mac OS X

There are a few steps we have to do first to get the necessary tooling.

## Install `geth` (go-ethereum)

The easiest way to get set up with the Go implementation of Ethereum (the most popular and well-supported) is to use Mac's official unofficial package manager `brew`:

    brew update
    brew upgrade
    brew tap ethereum/ethereum
    brew install ethereum

## Sync with Ethereum mainnet (optional)

Most of us will be running this on our laptops. Since disk space (?) and bandwidth are probably at a premium, we will use the fast-sync option to download the full blockchain. 

    geth --fast --cache=1024 --jitvm console

<br />

# Create private blockchain

The Ethereum mainnet public blockchain, if synced, will be sitting in the default directory of `~/Library/Ethereum/geth/chaindata`. You can poke around there if you'd like. For our own blockchain, we will need to bootstrap an initial "genesis block" with our own configurations, and have our machine set up to mine (if Proof of Work; called validating if Proof of Stake).

## Create genesis block configuration

A genesis block is defined by parameters in a json file. We can put this anywhere on our machine, so for this guide we will use a directory `~/eth-private`. Inside of this directory, create a new json file like the following. Brief explanations of each parameter below, for full details read the [reference](#reference) docs.

```
{
    "config": {
        "chainId": 15,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    },
    "nonce": "0x0000000000000042",
    "timestamp": "0x0",
    "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "gasLimit": "0x8000000",
    "difficulty": "0x400",
    "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "coinbase": "0x3333333333333333333333333333333333333333",
    "alloc": {}
}
```

`chainId`: The "id" of our private blockchain. An arbitrary number but we don't want it to conflict with the public ones (mainnet is "1").

`xxxBlock`: Configurations that take into account protocol changes that have happened since Ethereum's creation.

`nonce` and `mixhash`: The "Proof of Work" that needs to be done on the genesis block. Since it is the genesis block, we set this somewhat arbitrarily.

`gasLimit`: Upper bound of gas consumption for blocks in our chain

`difficulty`: How hard it is to find a valid block under Proof of Work methodology. The lower it is, the faster we will be able to mine and confirm transactions

`coinbase`: Address that mining rewards are sent; can be anything here since each miner sets their own rewards address

`alloc`: Initial "pre-mined" Ether that can be sent to arbitrary addresses. We can allocate ourselves a million Ether if we wanted to.

## Initialize the genesis block

Now we are ready to initialize our private blockchain! Fire up a new terminal, navigate to our new directory with the genesis config file `~/eth-private` and enter in the following command:

`geth --datadir "~/eth-private" --identity "Private" --networkid 15 --nodiscover --maxpeers 0 init genesis.json`

`--datadir`: Specifies where we want to store our blockchain data (recall that the mainnet directory is at `~/Library/Ethereum/geth/chaindata`)

`--identity`: What we call our private network

`--networkid`: How we reference which network we want to connect to (recall that we set this in the genesis config)

`--nodiscover`: Prevent others from mistakenly (or purposefully?) seeing our private network

`--maxpeers 0`: Prevent others from mistakenly (or purposefully?) connecting to our private network

If everything worked correctly, we should see a confirmation that looks like

<img src="/assets/img/2017/10/Screen-Shot-2017-10-02-at-10.18.19-AM.png" width="100%" />

## Create an address and begin mining

Now we can use the Geth command line tools to create a new address for ourselves and begin mining to get some ether. Invoke the Geth console with the same parameters that we used for initializing the network:

`geth --datadir "~/eth-private" --identity "Private" --networkid 15 --nodiscover --maxpeers 0 console`

Feel free to play around with the Geth console commands to get more familiar with the system. To proceed, create a new address with an arbitrary password:

`personal.newAccount("ourarbitrarypassword")`

Then set our new address as the "coinbase" used for our mining:

`miner.setEtherbase(personal.listAccounts[0])`

Now we can begin mining with our machine; remember that we set our difficulty in the genesis block to `0x400` so we should be mining blocks very quickly.

`miner.start()`

## Check ETH balance

We should have a lot of ETH after just a minute of running the miner. Leave the miner terminal instance open and start a new terminal window. We can connect to the same network instance into the Geth console and check our balance that way.

`geth --datadir "~/eth-private" --identity "Private" --networkid 15 --nodiscover --maxpeers 0 attach ipc:~/eth-private/geth.ipc`

Note that we used the `attach` command and passed another argument `ipc:`; the former is used to reference the Geth instance that is already running (our miner) and the latter is to specify the "socket" location being used for the network connection.

We can run the follow two commands to get our current running balance of our fake Ether:

    primary = eth.accounts[0]
    web3.fromWei(eth.getBalance(primary), "ether");

Imagine if all of those Ether were actually worth something ;)

# Conclusion

And that's it! We've successfully created our own Ethereum private local testnet, with a genesis block, address, and miner. If you use something like Mist or Ethereum Wallet, you can run the geth command from above first (without console or attach commands) before starting them, and the applications will both automatically connect to the private network.[^1] Then we can start testing our own smart contract deployments.

[^n]: If you have trouble connecting with Mist or Ethereum Wallet, try running the applications from the command line with the --rpc flag pointed at the IPC location (ie. /Applications/Ethereum\ Wallet.app/Contents/MacOS/Ethereum\ Wallet --rpc ~/eth-private/geth.ipc)

Stay tuned for the next tutorial: **Writing smart contracts**

<br />

> *Like this tutorial? Any tips are greatly appreciated!*<br />
*ETH*: `0x95c81f04d214330F687EBa412fF4fbb26ca9d708`<br />
*BTC*: `15kR6ty4TLi5bxm2r6gUxSJvsFQkNEwxf8`<br />

---

# References
- Ethereum Homestead guide: [Connecting to the Network](https://github.com/ethereum/homestead-guide/blob/master/source/network/connecting-to-the-network.rst#using-geth)
- go-ethereum Github wiki's [Private network](https://github.com/ethereum/go-ethereum/wiki/Private-network)
- StackExchange [Genesis block explanation](https://ethereum.stackexchange.com/questions/2376/what-does-each-genesis-json-parameter-mean)
- Ethdocs [Test networks](http://ethdocs.org/en/latest/network/test-networks.html)
- Souptacular gitbooks [Private chain](https://souptacular.gitbooks.io/ethereum-tutorials-and-tips-by-hudson/content/private-chain.html)
- StackExchange [Fatal: invalid genesis file: hex string has odd length](https://ethereum.stackexchange.com/questions/16145/fatal-invalid-genesis-file-hex-string-has-odd-length)
- StackExchange [When is the geth.ipc file produced?](https://ethereum.stackexchange.com/questions/1492/when-is-the-geth-ipc-file-produced)
- StackExchange [In a private blockchain, why do miners keep adding empty blocks to the blockchain?](https://ethereum.stackexchange.com/questions/6648/in-a-private-blockchain-why-do-miners-keep-adding-empty-blocks-to-the-blockchai)