---
layout: post
title: Blockchain, Bitcoin, and Ethereum ELI5 (Explained Like I'm Five)
featured: true
image: "/assets/img/2017/05/blockchain-ad-placeholder-b27dc1896d7c880e90ebeb3ebb64a96f5053865b.jpg"
date: '2017-01-17 05:19:00'
tags:
- blockchain
- bitcoin
- btc
- eli5
- ethereum
- eth
- cryptocurrency
- crypto
---

*Last updated: 14 Dec 2017*

<br />

# Table of Contents

- [Bitcoin ELI5](#bitcoineli5)
 - [Buying Bitcoin](#buyingbitcoin)
- [Blockchain ELI5](#blockchaineli5)
- [Ethereum ELI5](#ethereumeli5)

<br />

---

# TL;DR

**Blockchain** is a ledger of transactions that everyone owns and contributes to.

**Bitcoin** is a digital currency with a fixed supply built on blockchain technology, and has a few nice features that people like so they give it value.

**Ethereum** is a platform that lets anyone build "decentralized applications" on top of their blockchain technology, and runs on its own currency called Ether.

<br />

> There's lots to learn in this post. To help you remember, try my app **[Harvest](https://harvest.li): Take Notes and Learn Passively**. You can write or highlight any notes, save them, and automatically receive reminders on an optimal learning schedule.<br />
<a href="https://harvest.li"><img src="/assets/img/2017/09/harvest-icon.png" width="40" /></a>

<br />

It started with Bitcoin: the first mainstream digital currency that exploded into popularity in 2013, when the price of a single Bitcoin (BTC) went from $10 to over $1000 at its peak. Over the next year, BTC's steady decline back, losing 75% of its value to $250, was equally as tumultuous.

# Bitcoin ELI5

<script type="text/javascript" src="https://files.coinmarketcap.com/static/widget/currency.js"></script><div class="coinmarketcap-currency-widget" data-currency="bitcoin" data-base="USD" ></div>

[Bitcoins](https://bitcoin.org/en/) are digital coins that only have value if people give it value; this means that if no one would trade you anything for a Bitcoin, then it would be worthless. So why do people give Bitcoin any value? In short,

1. **Bitcoins are scarce** (there will only ever be 21 million of them). Scarcity means that no central authority, like the US government for US dollars, can create more coins to inflate away your current Bitcoin value. People (called "Miners") earn Bitcoins by helping verify Bitcoins that are sent have not already been sent elsewhere (via the [blockchain](#blockchaineli5)), which also means that once we reach the 21 million limit, sending Bitcoins will cost more Bitcoins (usually a fraction of one) as a fee paid to Miners to keep them working.

2. **Bitcoins are fast to transact in** (sending a coin to someone else takes 10 minutes to verify). Fast transactions means you can send and receive money without going through a third party like a bank. Handing over real cash is obviously faster, but then you would need to carry cash around and transact in person. If someone sends you a Bitcoin, you can trust that it has not already been sent elsewhere because a Miner will have verified that Bitcoin and told everyone else that the Bitcoin now belongs to you. Everyone knows where any Bitcoins are at any point in time.

3. **Bitcoins are anonymous** (no one knows who you are or how many Bitcoins you have). Anonymity means you can do what you want with your Bitcoins without anyone else knowing. Of course, if you tell someone what your wallet ID is, then they can trace all transactions from that wallet back to you. So don't tell anyone which wallet is yours if you want privacy. You can create as many different wallets as you want.

All of those factors make Bitcoins a currency that people can use for buying and selling things, and possibly for storing wealth.

<br />

## Buying Bitcoin

Want to buy some yourself? There are tons of ways to get bitcoin, but the easiest way is to use the most established crypto platform in the USA, **[Coinbase](https://www.coinbase.com/join/527af8b8e59746fe9c00003f)**.

> *Help me help you! **[Sign up for Coinbase](https://www.coinbase.com/join/527af8b8e59746fe9c00003f)** using my referral code (already linked) and we both get $10!*

<a href="https://www.coinbase.com/join/527af8b8e59746fe9c00003f" target="_blank"><img src="/assets/img/2017/08/coinbase.png" width="100%" alt="coinbase logo" /></a>

On Coinbase, you'll be able to purchase BTC using conventional fiat methods including PayPal, Bank Account (US), and Credit/Debit Card; each has different buying times and limits, generally the longer the buying time the higher the limit.

![coinbase payments](/assets/img/2017/08/coinbase-payments.png)

---

Now that you know something about Bitcoin, how does the digital currency actually work? Underneath it all is something called Blockchain. Here are some high-level concepts of the underpinning technology without gory technical details.

<br />

# Blockchain ELI5

Bitcoin is built on top of a technology called a [blockchain](https://en.wikipedia.org/wiki/Blockchain_(database)). Think of a blockchain as a digital ledger of transactions, with a copy stored on every single user's computer. Every time a new transaction takes place, a new record is added to the ledger, and an update is beamed out to the rest of the network in a peer-to-peer fashion. In this way, a blockchain gets decentralization since everyone has a copy of the ledger. No single entity has monopoly over the validity of transactions which also means there is no single point of failure, barring some apocalyptic event. If someone offers me a unit of cash of a currency built on a blockchain, I can simply check the current state of that blockchain's ledger to see if the unit of cash is valid[^1] and has not already been spent. If it is indeed valid, then I accept the transaction, add a new record to my ledger, and send an update of the new state to the other nodes in our network.

And that's a blockchain. Simple in concept and with many ways to implement for use cases. A lot of hard problems need to be solved for successful implementations, and Bitcoin is just currently the most popular of them. For a great high-level read on the real-world impact of blockchain, check out [A beginner's guide to institutional cryptoeconomics](https://medium.com/@cryptoeconomics/the-blockchain-economy-a-beginners-guide-to-institutional-cryptoeconomics-64bf2f2beec4).

[^1]: A big question at this point is when there are conflicts in the ledger, how do we know which version is correct? My version says a transaction took place, while yours shows a different one. This conflict is the [double-spending](https://en.wikipedia.org/wiki/Double-spending) problem, an obvious method to try and manipulate the system. Blockchain technology inherently does not solve this problem; implementations do. Bitcoin, for example, solves the double-spending problem by using [proof-of-work](https://en.wikipedia.org/wiki/Proof-of-work_system).

---


And now we get to the new kid on the block(chain), Ethereum. Investors and the public are treating it like another digital currency, but Ethereum can do a lot more than that.

# Ethereum ELI5

<script type="text/javascript" src="https://files.coinmarketcap.com/static/widget/currency.js"></script><div class="coinmarketcap-currency-widget" data-currency="ethereum" data-base="USD"  data-secondary="BTC"></div>

If Bitcoin was made as a new currency for people, then Ethereum was made as a new _application platform_ for people. What does application platform mean? It means anyone can build any kind of application on top of Ethereum, and use Ethereum's blockchain as its "digital ledger" to store information. So yes - if you wanted to, you could build your very own Bitcoin version on top of Ethereum.

Because we still need "Miners" (people ie. their computers) to validate transactions flowing throughout the network, we need to make sure Miners are still incentivized to do so. Bitcoin used Bitcoins as a reward. Ethereum has a similar concept - its main currency is called **ether** (ETH). Ether can be sent back and forth between accounts, just like Bitcoins, and Miners validate each transaction to make sure an ETH hasn't already been sent elsewhere, receiving a bit of ETH as their reward.

The biggest feature with Ethereum however, and the one that makes it an application platform instead of a mere currency, is that there can be accounts _owned by code_ (called "smart contracts") and not owned by people. How does that work? We said earlier that anyone can build any application; accounts owned by code are exactly these applications, written by people and doing things using ETH as fees for doing them.

An example of an application is a "crowdsale" - say you want to raise a certain amount of money from people for a project or product, Kickstarter style. By specifying a target amount and a deadline, participants can pledge ETH to an account, which in turn will hold the ETH and only release the ETH to your account if it hits the target amount by the deadline. Otherwise the ETH is returned.

<img src="/assets/img/2017/06/Screen-Shot-2017-06-04-at-10.20.05-PM.png" width="100%" alt="ethereum price" />

Ethereum's popularity (and price) has grown monstrously in the first half of 2017, as new applications are being created and investors and the public become more aware of its features. Look forward to continued innovation in this space!

<br />

---

# TL;DR

**Blockchain** is a ledger of transactions that everyone owns and contributes to.

**Bitcoin** is a digital currency with a fixed supply built on blockchain technology, and has a few nice features that people like so they give it value.

**Ethereum** is a platform that lets anyone build "decentralized applications" on top of their blockchain technology, and runs on its own currency called Ether.

<br />

> *Like this post? Fund future posts by contributing to my tip jars :)*<br />
*BTC*: `15kR6ty4TLi5bxm2r6gUxSJvsFQkNEwxf8`<br />
*ETH*: `0x95c81f04d214330F687EBa412fF4fbb26ca9d708`