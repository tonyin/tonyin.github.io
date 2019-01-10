---
layout: post
title: Neon Exchange (NEX) Whitepaper Summary
image: "/assets/img/2017/12/nex_logo.jpg"
date: '2017-12-30 06:32:40'
tags:
- neo
- crypto
- whitepaper
- dex
- nex
---

This post summarizes the [Neon Exchange](https://neonexchange.org/) [whitepaper](https://neonexchange.org/pdfs/whitepaper_v1.1.pdf) (as of v1.1, 23 Nov 2017 publication) and evaluates the project based on a number of criteria listed below. The details here do not constitute any investment recommendations and is purely for informational purposes. Subscribe below or [follow me on Twitter](https://twitter.com/tonyin) for more of this.

---

## Summary
NEX is a cryptocurrency exchange built on the [NEO platform](http://neo.org/) that combines the high performance of a traditional centralized exchange with the trust and security of a decentralized exchange. NEX uses three core components: 1) Provable fair off-chain order matching, 2) Batched on-chain trade commitment, and 3) Token exchange layer. The ultimate vision is to enable decentralized banking by offering not only trading but general secure asset management.

> **NEO's "killer" asset exchange DApp**

<br />

## Evaluation

<table>
<tr><th><strong>Criteria</strong></th><th><strong>Score /10</strong></th></tr>
<tr><td><a href="#team">Team</a></td><td>9</td></tr>
<tr><td><a href="#partnerships">Partnerships</a></td><td>5</td></tr>
<tr><td><a href="#technology">Technology</a></td><td>8</td></tr>
<tr><td><a href="#economics">Economics</a></td><td>9</td></tr>
<tr><td><strong>OVERALL</strong></td><td>7.75</td></tr>
</table>

Important Dates:

* Feb 2018: Open source ICO platform with KYC
* Q1 2018: ICO takes place

<br />

---

## Team
[Co-founders](https://neonexchange.org/#the-team) are all [CoZ (City of Zion](https://twitter.com/coz_official)), a talented community of independent NEO developers mostly based in Europe and the US. [Canesin ](https://www.linkedin.com/in/canesin) and [Fast](https://www.linkedin.com/in/ethanfast) in particular are both active in the NEO communication channels and readily answer questions.

> **CoZ team with proven record of execution and existing working relationship with NEO core team**

<br />

## Partnerships
NEO — Smart contracts and trade commitments are on the NEO blockchain
Fiat processing — Anticipated partnerships for allowing fiat use

> **No partners announced thus far aside from NEO**

<br />

## Technology
* **Off-chain Order Matching**
	* Dedicated service that handles the order book and order matching
	* Orders are matched using a deterministic algorithm (price-time)
	* Elixir/Erlang stack
	* Uses a network of independent “supervisor services” that monitor the order matching engine, as well as each other, to detect suspicious behavior
	* “Provable fair off-chain matching” — public ledger of orders, deterministic matching algorithm, and reward for proving incorrect matches
	* No fees for liquidity making (resting orders), graduated fees (up to 0.25%, based on activity) for liquidity taking (trades against resting orders)
* **On-chain Trade Commitments**
	* Trades from off-chain order matching are batched and committed to on-chain smart contract
	* Performance can theoretically be up to 100k txs per second
* **Token Exchange Layer**
	* NEO uses UTXO which allows for fast node tx verification but hard for smart contracts to interact with NEO and GAS global on-chain assets; hence need to convert global assets into NEP-5 standard for fast processing
	* Smart contract that exchanges global assets 1:1 with NEP-5 smart contract tokens
	* Users deposit global assets (eg. NEO or GAS) which allows them to trade with equivalent NEP-5 asset (eg. XNEO or XGAS)
	* Users can withdraw as many global assets as they have of the equivalent NEP-5 asset
* User account private keys stored encrypted and client-side

> **Holy grail of trading exchange — performance + trust + security**

<br />

## Economics
* 50 million NEX tokens
* 25 million sold to public
* Individual cap (initial thoughts $5-10k)
* Stake tokens to get a share of revenue; can choose length of staking time for higher return

> **Simple and straightforward token allocation with staking details to be clarified**

<br />

## Q&A
**Q**: Off-chain order matcher gets compromised. Trades are executed not according to price-time precedence. User gets to withdraw their assets. How to avoid?<br />
**A**: A network of “[supervisor services](http://erlang.org/doc/man/supervisor.html)” monitor the order matching engine, as well as each other, to detect suspicious behavior

**Q**: How do NEX internal NEP-5 equivalents of outside global assets get supported?<br />
**A**: [NEP-4](https://github.com/neo-project/proposals/blob/master/nep-4.mediawiki) allows for dynamic calling of undefined smart contracts, so any trading pair can be declared if valid

**Q**: Presale?<br />
**A**: There is no pre-sale, we only are accepting partnerships with business that have licenses to do fiat to crypto pairs in main crypto markets.

**Q**: How to buy?<br />
**A**: Fiat pairs will be launched together with the open source of the fiat system right before the ICO time, NEX itself will not do the fiat, we will have an innovative technology using partnerships and smart contracts.

**Q**: ICO caps?<br />
**A**: ICO will happen, there will be an individual cap, it will be low for ICO standards and the goal is to have the most people we can participating.

<br />

---

## Useful Links
* [NEX Website](https://neonexchange.org/)
* [NEX Whitepaper](https://neonexchange.org/pdfs/whitepaper_v1.1.pdf)
* [NEX Twitter](https://www.twitter.com/neonexchange)
* [NEO Reddit](https://www.reddit.com/r/NEO/)
* [NEO Discord](https://discord.gg/R8v48YA)
* [Guide to Buying NEO](https://tonyy.in/guide-to-buying-antshares-neo-ans-on-bittrex-exchange/)

<br />

> Like this post? [Upvote on Steem](https://steemit.com/cryptocurrency/@aeto/neon-exchange-nex-whitepaper-summary) to keep 'em coming

> Tip jar for my personal NEX fund:

> NEO: `AdMuBsegpcFkFZ8HyLWrJ3wSifCx3H5k8p`