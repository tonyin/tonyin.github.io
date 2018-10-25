---
layout: post
title: Crypto Weekly Roundup 2/15/18
date: '2018-02-15 16:28:30'
tags:
- crypto
- cwr
---

<br />

## Metrics
[Total Market Cap](https://coinmarketcap.com/charts/): $471 billion (+21% w/w)<br />
[MC 7-Day Range](https://coinmarketcap.com/charts/): $98 billion (-48% w/w)<br />
[Bitcoin Dominance](https://coinmarketcap.com/charts/#dominance-percentage): 35.3% (-0.3 w/w)

## Summary
- BitGrail “Loses” 17M Nano (or how shitty code re-enables the double-spend problem)
- MEW Forks to MyCrypto (an exact copy in this case)
- A Feast of Forks (Classic Private Callisto Cash… did I get that right)

## BitGrail “Loses” 17 million Nano (fmr. RaiBlocks)
[Nano](https://nano.org/en) ([$XRB](https://coinmarketcap.com/currencies/raiblocks/)), formerly RaiBlocks before the rebrand, is a currency token known for its near-instant speed and zero-fee transactions. It went from a small project on [one small Italian exchange](https://bitgrail.com) to a [$2 billion+ market cap in less than a month](https://coinmarketcap.com/currencies/raiblocks/) in December. On Friday, that small exchange BitGrail [announced a suspension](https://bitgrail.com/news) on all trading as its “internal checks revealed unauthorized transactions which led to a 17 million Nano shortfall” (price was $10 per XRB, or a $170 million shortfall, at time of announcement). [Redditors blame](https://www.reddit.com/r/nanocurrency/comments/7x1g8x/after_researching_what_is_currently_available_ive/)  the man behind BitGrail, [“Bomber”](https://twitter.com/bomberfrancy), for [writing shitty code](https://www.reddit.com/r/nanocurrency/comments/7widwu/there_is_a_lot_of_talk_about_a_bitgrail_hacker/), getting hacked (dating back to October), and/or using his exchange to manipulate prices to recoup losses (arbitraging between BitGrail and others). The Nano Core team [has investigated the hack](https://medium.com/@nanocurrency/bitgrail-insolvency-update-2-11-18-9349c9fe1281) and confirmed the validity of all transactions (and rejecting a hard fork a la Ethereum DAO), inferring suspicious activity from BitGrail. As a reminder just a few weeks ago another exchange, Coincheck, had all of their NEM hacked. Stay safe out there.

## MyEtherWallet Forks To MyCrypto
Founder issues is the #1 reason why startups fail (apocryphal) and the crypto world is no exception. [MyEtherWallet](https://www.myetherwallet.com/) (MEW) has been the de facto “mainstream” Ethereum wallet for ETH and ERC-20 tokens, due to its lightweight nature (client side, does not sync its own blockchain) and first-mover advantage. On Thursday the [original MEW Twitter account](https://twitter.com/mycrypto), with 80k followers, [suddenly changed](https://twitter.com/myetherwallet/status/961792085060808704) its handle to "@mycrypto". In an environment of rampant hacks and scams, this change was concerning. One of the cofounders (?) [@tayvano](https://twitter.com/tayvano_) soon [published an article](https://medium.com/mycrypto/mycrypto-launch-6a066bf41093) introducing [MyCrypto](https://mycrypto.com/) and a background of MEW, though with no mention of the reason behind the split. The original founder (?) [@kvhnuke_](https://twitter.com/kvhnuke_) [published his own article](https://www.reddit.com/r/ethereum/comments/7wgnds/official_myetherwallet_statement/) about the background of MEW and explained that the partnership had ended, though the Twitter handle change was unexpected (with new migrated account [@myetherwallet](https://twitter.com/myetherwallet)). For now, MyCrypto is purportedly an exact replica of MEW.

Regardless of how the partnership ended, there should not have been a sudden takeover switch of as important a public communication channel as the Twitter account. On Wed the ex-founders seemed to have come to an agreement and [swapped the Twitter handles back](https://twitter.com/myetherwallet/status/963927289938374656), with MyCrypto “hopeful that the new team at MyEtherWallet will use their reach of over 80k dedicated cryptocurrency followers wisely.” Salty!

## A Feast of Forks
Speaking of forks... there are three major forks (/airdrops) coming up, and the anticipation of each has induced some interesting price movements in their respective coins.

**ZClassic —> Bitcoin Private**<br />
[ZClassic](https://zclassic.org/) ([$ZCL](https://coinmarketcap.com/currencies/zclassic/)) created by [@HeyRhett](https://twitter.com/HeyRhett), is itself a fork of [Zcash](https://z.cash/) ([$ZEC](https://coinmarketcap.com/currencies/zcash/)) which is a currency coin known for private transactions (unlike Bitcoin which has fully transparent transactions). Rhett’s main idea for ZCL was to remove the 20% fee in ZEC that was automatically given to the founders with each block, and instead give it to the miners. Okay, admirable redistribution move — but more ambitiously Rhett wanted to bake private transactions *into Bitcoin itself* with a new coin called [Bitcoin Private](https://btcprivate.org/) ($BTCP) combining features from both ZCL and BTC. The twist here is that holders of ZCL *and* BTC will receive BTCP in a 1:1 ratio each (despite the price difference) at a block snapshot sometime Feb 28. The fork announcement in late Dec 2017 saw a 3x increase in ZCL price in one day. Critics call the project [a scam to pump ZCL](https://twitter.com/nic__carter/status/957785010832052224) with an inevitable dump after the snapshot. Short term however ZCL holders don’t care as the price has almost doubled to $160. [Comprehensive Reddit FAQ](https://www.reddit.com/r/BitcoinPrivate/comments/7xed60/please_read_zclassic_bitcoinprivate_snapshotfork/).

**Ethereum Classic —> Callisto**<br />
[Ethereum Classic](https://ethereumclassic.github.io/) ([$ETC](https://coinmarketcap.com/currencies/ethereum-classic/)) and Callisto is another case of a fork of a (technically original) fork — in June 2016 the [now-infamous DAO Hack](https://www.coindesk.com/understanding-dao-hack-journalists/) prompted a hard fork of Ethereum to recover the lost DAO proceeds. [Hardcore idealists](https://ethereumclassic.github.io/assets/ETC_Declaration_of_Independence.pdf) continued development of the original fork in the spirit of immutability, and thus was born Ethereum Classic. On Jan 16, the [developers behind ETC](https://github.com/EthereumCommonwealth) announced the [Callisto Network ($CLO)](https://www.reddit.com/r/EthereumClassic/comments/7qs9ui/callisto_network_announcement/) fork which will credit ETC holders a 1:1 ratio of CLO at block 5500000 (Mar 5). According to the [CLO whitepaper](https://drive.google.com/file/d/16sW_0YajCedBdLvr9jmgJqE9L-SzuYKq/view), Callisto aims to be a research and experimental blockchain to help improve the overall ETC ecosystem. In particular the paper mentions a smart contract auditing department, cold staking protocol, and governance system (Nov 11). ETC has [doubled in price](https://coinmarketcap.com/currencies/ethereum-classic/) since a week ago but the overall market has recovered some and besides, [this Redditor is unconvinced](https://www.reddit.com/r/EthereumClassic/comments/7xgfvv/when_is_this_airdropfork_thats_driving_up_the/).

**Litecoin —> Litecoin Cash**<br />
If you didn’t think [Litecoin](https://litecoin.com/) ([$LTC](https://coinmarketcap.com/currencies/litecoin/)) could get any lighter, wait until this coming Sunday when [Litecoin Cash](https://litecoinca.sh/) (air)drops. Holders of LTC will receive $LCC at a 10:1 ratio (10 LCC for 1 LTC) at block 1371111 (Feb 18). The [biggest change in Litecoin Cash](https://themerkle.com/what-is-litecoin-cash/) is the hash algorithm to match Bitcoin’s SHA-256, which allows mostly old Bitcoin ASIC miners to now dominate the new coin’s mining. [Charlie Lee](https://twitter.com/SatoshiLite), chikun, has [denounced the fork](https://twitter.com/satoshilite/status/958170338621145089) as a scam, which is a bit harsh as LCC represents its features quite transparently. Nonetheless LCC will have a hard time with adoption — not a single wallet has been published yet that supports LCC despite the fast-approaching fork date, and LTC functions perfectly well as a payment coin. $LTC has rallied almost 50% alongside the overall market recovery.

## NEO ONT Airdrop
And a bonus one for my favorite coin [$NEO](https://coinmarketcap.com/currencies/neo/) — [holders will receive](https://neo.org/blog/details/3061) [Ontology’s $ONT](https://ont.io/) at a 0.2:1 ratio at block 1974823 (Mar 1).

See you guys next week —

<br />

*Like this summary?<br /> [Upvote it on Steemit](https://steemit.com/cryptocurrency/@aeto/aeto-s-crypto-weekly-roundup-2-15-18) and [follow me on Twitter](https://twitter.com/tonyin) for more of this.*<br />*Last week: [Crypto Weekly Roundup 2/8/18](https://tonyy.in/crypto-weekly-roundup-2-8-18/)*<br />*All Editions: [Crypto Weekly Roundups](https://tonyy.in/tag/cwr/)*

*Crypto Weekly Roundup is for informational purposes only and does not constitute any investment recommendations.*