---
layout: post
title: Crypto Weekly Roundup 3/22/18
date: '2018-03-22 15:41:00'
tags:
- crypto
- cwr
- newsletter
---

<br />

## Metrics
[Total Market Cap](https://coinmarketcap.com/charts/): $330 billion (+2% w/w)<br />
[MC 7-Day Range](https://coinmarketcap.com/charts/): $81 billion (-13% w/w)<br />
[Bitcoin Dominance](https://coinmarketcap.com/charts/#dominance-percentage): 44.2% (+1.7 w/w)

## Summary
* Big ETH ICO Dumps, Watch Addresses For More
* G20 Meeting: Crypto As Taxable Assets, No Regulations Needed (Yet)
* Bitcoin “Lightning” Network Goes Mainnet

## Big ETH ICO Dumps
The market has undergone a severe downturn in the past couple of weeks, dropping about 25% to $330 billion total MC today. Magical crypto friend [WhalePanda](https://twitter.com/WhalePanda) [went looking for reasons](https://twitter.com/WhalePanda/status/975284097064079360) and found out that some [big ETH ICO projects](https://twitter.com/claptrapxl/status/975338672131223552) (eg. [$EOS](https://onchainfx.com/asset/eos)) may have been [dumping their holdings](https://sanbase-low.santiment.net/projects). We got Mt. Gox BTC addresses to track from last week, now we got ourselves some [ETH addresses](https://docs.google.com/spreadsheets/d/1eOh_lT8vKj0IuUFxOftiSjcItViv0ZGHphYApXHJhoM) to as well.

## G20 Meeting: Crypto As Taxable Assets, No Regulations Needed (Yet)
Reuters was back to its old tricks last week [stirring up warnings](https://www.reuters.com/article/us-g20-communique-draft-cryptocurrency-e/exclusive-g20-financial-heads-to-urge-crypto-asset-monitoring-to-safeguard-financial-stability-idUSKCN1GP2PQ) about the then-[upcoming G20 meeting](https://www.g20.org/en) for finance ministers and central bank governors. The message (from a “draft communique”) was the usual, acknowledging that the “technological innovation behind crypto-currencies” (aka blockchain) was promising but that the current manifestation of crypto assets led to scams, tax evasion, money laundering, and terrorist financing.

The actual outcomes from the meetings were neutral and more restrained as world leaders agreed to [continue monitoring](https://www.reuters.com/article/us-g20-argentina-bitcoin/g20-agrees-to-monitor-cryptocurrencies-but-no-action-yet-idUSKBN1GW2IO) the space, and that [crypto assets were “assets” and not “currencies”](https://www.bloomberg.com/news/articles/2018-03-20/when-is-a-bitcoin-not-a-bitcoin-when-it-s-an-asset-says-g-20) (implying capital gains taxes). No concrete multinational regulations were agreed upon. In particular, the Financial Stability Board (FSB) Chair noted that crypto assets  were <1% of the world’s economy even at its peak ([about $800 billion USD](https://coinmarketcap.com/charts/)), and that “crypto-assets do not pose risks to global financial stability at this time”; the focus instead would be on [reviewing existing rules](https://www.cnbc.com/2018/03/18/reuters-america-g20-watchdog-focuses-on-rules-review-holds-fire-on-cryptocurrencies.html).

Cynically, countries really just want their cut (taxes).

## Bitcoin “Lightning” Network Goes Mainnet

![lightning-nodes](/assets/img/2018/03/lnd-nodes.png)
*Snapshot of Bitcoin Lightning-enabled nodes*

Bitcoin ([$BTC](https://onchainfx.com/asset/bitcoin)), like its younger sibling Ethereum ([$ETH](https://onchainfx.com/asset/ethereum)), has faced a daunting [scalability problem](https://en.wikipedia.org/wiki/Bitcoin_scalability_problem) since its rise to mainstream attention. Every Bitcoin transaction needs to be verified and broadcasted on the blockchain itself, leading to a bottleneck in
1. How fast miners can validate transactions (which is dynamically adjusted to target one block of transactions every 10 minutes), and more importantly,
2. How many transactions can fit into a single block.
Bitcoin users can thus either pay a [higher transaction fee](https://bitinfocharts.com/comparison/bitcoin-transactionfees.html) so that miners will prioritize their transactions ahead of others, or simply [wait until miners get to them](https://blockchain.info/charts/avg-confirmation-time). Neither are good experiences. [Block size limit](https://en.bitcoin.it/wiki/Block_size_limit_controversy) is one of the main reasons why Bitcoin Cash ([$BCH](https://onchainfx.com/asset/bitcoin-cash)) hard-forked from BTC in August 2017 — BTC has a [1 MB block size limit](https://github.com/bitcoin/bitcoin/commit/a30b56ebe76ffff9f9cc8a6667186179413c6349), whereas BCH [increased this limit to 8 MB](https://www.bitcoincash.org/#features). ([Chart of BTC vs BCH block sizes in practice](https://bitinfocharts.com/comparison/size-btc-bch.html)).

[Lightning network](https://lightning.network/) is one of the primary solutions for blockchain transaction scalability, a so-called “second layer” protocol meaning transactions are happening on a layer above the native blockchain itself. Two users can open a “[state channel](http://www.jeffcoleman.ca/state-channels/)” between them using Lightning, allowing them to send and receive their deposited Bitcoin balances to each other without having to commit each transaction to the blockchain (thus requiring no miners to validate). The state channel can be closed at any time by either user, and only the final balance needs to then be committed to the blockchain. Here is a great [primer video](https://www.youtube.com/watch?v=UYHFrf5ci_g) on how Lightning works, and a small conspiracy theory about who is really behind its development (hint: it is not cypherpunk devs).

Since the publication of the Jan 2016 [whitepaper](http://lightning.network/docs/), multiple parties have taken up the Bitcoin implementation of Lightning with [Lightning Labs](http://lightning.engineering) and its [Lightning Network Daemon (`lnd`)](https://github.com/lightningnetwork/lnd) at the forefront. Last Tuesday, [Lightning Labs announced](https://blog.lightning.engineering/announcement/2018/03/15/lnd-beta.html) the [`lnd` beta](https://github.com/lightningnetwork/lnd/releases/tag/v0.4-beta) and mainnet launch, a huge step towards [real-world usage](https://lnmainnet.gaben.win/), though important to note that the beta is aimed at “developers of future Lightning applications (Lapps) along with technical users and prospective routing node operators”. Heavily trafficked nodes (eg. exchanges, payment gateways) would benefit the most from the increased speed and reduced cost, with the possible tradeoff of increased centralization (you need a lot of deposited Bitcoin to efficiently operate the nodes). The scalability enabled by Lightning is crucial for wider Bitcoin usage, such as p2p payments, aside from the long-term “store of value” use case. Lightning has already been or is being implemented on other coins like Ethereum ([Raiden](https://raiden.network/) [$RDN](https://coinmarketcap.com/currencies/raiden-network-token/)) and Litecoin ([$LTC](https://onchainfx.com/asset/litecoin)).

See you guys next week —

<br />

*Like this roundup?<br /> Support me on [Medium](https://medium.com/crypto-weekly-roundup), [Steemit](https://steemit.com/cryptocurrency/@aeto/aeto-s-crypto-weekly-roundup-3-22-18), and [Twitter](https://twitter.com/tonyin) for more of this.*<br />*Last week: [Crypto Weekly Roundup 3/15/18](https://tonyy.in/crypto-weekly-roundup-3-15-18/)*<br />*All Editions: [Crypto Weekly Roundups](https://tonyy.in/tag/cwr/)*

*Crypto Weekly Roundup is for informational purposes only and does not constitute any investment recommendations.*