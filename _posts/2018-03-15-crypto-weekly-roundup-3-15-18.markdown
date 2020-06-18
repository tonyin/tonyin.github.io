---
layout: post
title: Crypto Weekly Roundup 3/15/18
date: '2018-03-15 16:15:00'
tags:
- crypto
- cwr
- newsletter
---

<br />

## Metrics
[Total Market Cap](https://coinmarketcap.com/charts/): $322 billion (-19% w/w)<br />
[MC 7-Day Range](https://coinmarketcap.com/charts/): $93 billion (+13% w/w)<br />
[Bitcoin Dominance](https://coinmarketcap.com/charts/#dominance-percentage): 42.5% (+0.6 w/w)

## Summary
* Mt. Gox Trustee Sold 35k BTC To Pay Creditors, Remaining 165k BTC Fate Unknown (But Probably Locked Up For A While)
* Ethereum EIP-721 Paves Way For More Kitties
* Keybase: Now Sponsored By Stellar

## Mt. Gox Strikes Again
[Mt. Gox](http://www.mtgox.com/) was the first large mainstream Bitcoin exchange in the world, dominating BTC transactions from 2010-2013; it also became the first epic meltdown of one as [850,000 BTC went missing or were stolen](https://en.wikipedia.org/wiki/Mt._Gox) during that time. The story is a long, torturous decline rife with withdrawal delays and deposit freezes, ending in a [bankruptcy filing](https://www.courtlistener.com/docket/4389854/mtgox-co-ltd/) (in both Japan and US) in early 2014. Residual funds of 200k BTC were held by a trust with their fate to be decided by the Japanese courts.

In the past week a [report of the Mt. Gox bankruptcy proceedings](https://www.mtgox.com/img/pdf/20180307_report.pdf) surfaced, showing that the trustee of the funds, Nobuaki Kobayashi, had sold 35k BTC (at an avg price of $10k per BTC) starting Sep 2017 to purportedly [cover the fiat-valued claims of creditors](https://www.trustnodes.com/2018/03/07/mt-gox-trustee-sold-half-billion-dollars-worth-bitcoin-bitcoin-cash), or about $400 per BTC the price at the time of bankruptcy. Paying back with fiat, ie. USD or JPY, would be easy due to the increase in price, but creditors are also clamoring for the remainder of BTC to be distributed. Ultimately it will be up to the Japanese courts on who gets what, which may take many more months ([more explanations in reddit comments](https://www.reddit.com/r/Bitcoin/comments/82moph/35_000_btc_of_the_200k_mtgoxbtc_were_sold_over/)).

Kobayashi dumping 35k BTC (or nominally $350 million USD) on the open market, as opposed to a [more orderly auction or OTC transaction](https://www.reddit.com/r/mtgoxinsolvency/comments/82ykgu/re_the_dumpening/), has been [criticized by the community](https://www.reddit.com/r/mtgoxinsolvency/comments/83gvr0/lets_admit_it_was_a_right_call_by_the_trustee_to/) and blamed for contributing to the current bear market. A Twitter user [drew arrows on a chart](https://twitter.com/matt_odell/status/971432146656202752) (reproduced below) to show a leading correlation between movement from the Mt. Gox wallets and subsequent market dips. 

![btc selling](/assets/img/2018/03/DXs4OekXcAYyg5b.jpg-large.jpeg)

Concerned traders made a [list of the remainder of the known Mt. Gox wallets](https://www.cryptoground.com/mtgox-cold-wallet-monitor/) to monitor the movement of funds: the theory is that if any BTC are moved, then it is an indication of future selling. No movement so far and there is [no expectation of it](https://www.reddit.com/r/BitcoinMarkets/comments/82r4v9/there_is_no_reason_for_the_mt_gox_trustee_to_sell/) in the near future as the trust now holds enough fiat to satisfy the fiat claims. The [next creditor’s meeting is on 26 Sep 2018](https://www.reddit.com/r/mtgoxinsolvency/comments/82n6hi/latest_update_7_march_2018_bankruptcy_proceedings/), where there will hopefully but unrealistically be more clarity on the fate of the money including the remaining 165k BTC.

So fear not! The Mt. Gox bear whale will be resting a while for now.

## Ethereum Implements NFT Standard
Non-fungible tokens (NFT) are exactly what they sound like — tokens that are unique and not “[fungible](http://www.dictionary.com/browse/fungible)” with another token. The best example of an NFT is [CryptoKitties](https://www.cryptokitties.co/), where each cryptokitty is represented by a unique token containing a hash value that contains all of the “genetic history” of the kitty. The [merging of EIP-721](https://github.com/ethereum/EIPs/pull/841) establishes a [standard way](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md) for Ethereum dApps to implement an NFT. New kitties!

## Keybase: Sponsored by Stellar
Crypto, meet crypto. Privacy chat darling [Keybase](https://keybase.io/) announced that it has [received funding from the Stellar Foundation](https://keybase.io/blog/keybase-stellar), with a promise of an integration with the Stellar platform later this year. Keybase is known for providing a free (for now) end-to-end encrypted chat, file-sharing, and git repository client for individuals and teams. They [raised $10+ million in 2015 led by a16z](https://keybase.io/blog/2015-07-15/keybase-raises-series-a) with the goal of making “crypto” (in the traditional sense) easy to use: Users can cryptographically verify their identity and [messages](https://keybase.io/encrypt) with Keybase’s client. [Discussions ensued](https://news.ycombinator.com/item?id=16545092).

## Google Bans Crypto Ads
Google has [announced a ban](https://support.google.com/adwordspolicy/answer/7648803?hl=en) on all “cryptocurrencies and related content (including but not limited to initial coin offerings, cryptocurrency exchanges, cryptocurrency wallets, and cryptocurrency trading advice”. This  ban follows a [similar move by Facebook](https://www.facebook.com/business/news/new-ads-policy-improving-integrity-and-security-of-financial-product-and-services-ads) several weeks back. Crypto is being rolled under “financial services” products deemed risky for ordinary people, like binary options and financial spread betting.

## Good Reads
* [Token-Curated Registries 1.0 – Mike Goldin](https://medium.com/@ilovebagels/token-curated-registries-1-0-61a232f8dac7)<br />
The OG guide to Token-Curated Registries, as well as a [1.1 followup](https://medium.com/@ilovebagels/token-curated-registries-1-1-2-0-tcrs-new-theory-and-dev-updates-34c9f079f33d). TCRs are a way to incentive curation of high-quality lists that users can trust, curators can get paid to maintain, and list candidates can benefit from via exposure.

* [Blockchain Proof-of-Work is a Decentralized Clock - Gregory Trubetskoy](https://grisha.org/blog/2018/01/23/explaining-proof-of-work/)<br />
In which the author argues that PoW is really just a way for users to track time, not in the traditional sense of atomic seconds, but in the probabilistic nature of finding a solution to the PoW puzzle and the “clock tick” of a new block.

See you guys next week —

<br />

*Like this roundup?<br /> Support me on [Steemit](https://steemit.com/cryptocurrency/@aeto/aeto-s-crypto-weekly-roundup-3-15-18), [Twitter](https://twitter.com/tonyin), and [Email](https://tonyy.in/subscribe/) for more of this.*<br />*Last week: [Crypto Weekly Roundup 3/8/18](https://tonyy.in/crypto-weekly-roundup-3-8-18/)*<br />*All Editions: [Crypto Weekly Roundups](https://tonyy.in/tag/cwr/)*

*Crypto Weekly Roundup is for informational purposes only and does not constitute any investment recommendations.*