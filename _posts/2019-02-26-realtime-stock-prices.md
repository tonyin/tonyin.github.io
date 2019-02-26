---
layout: post
title: Realtime stock prices
date: '2019-02-25'
tags:
- aeto-labs
- discord
---

I’ve already set up the [discord server bot](https://github.com/tonyin/aeto-bot) to get real-time crypto prices from Binance. Crypto is new enough that the API infrastructure for third party tools (especially automated trading) is table stakes; you won’t attract enough trade volume without good API support. Binance also happens to be consistently one of the top 5 exchanges by volume, so prices are going to be decent enough to be global best. Back in the real world however we need to figure out how to get real-time stock prices.

## Requirements

There are 3 main data feeds we care about:

* **1st level order book**: The current best bid and ask prices with corresponding volume at those levels.
* **2nd level order book**: The next levels of bid and ask prices with their volumes.
* **Trades**: Orders that have been matched by the exchange and removed from the order books.

For a discord bot, we probably only need the 1st level order book since we’re not doing anything crazy. We do need the feed to be real-time however.

I started by looking at what I think are where the stock trading volume happens: Nasdaq and NYSE.

## Primary Sources

Nasdaq’s site looks like it’s from the 90s. Some clicking around broken links took me to their [prices](https://www.nasdaqtrader.com/Trader.aspx?id=DPUSdata). Not keen on paying money for this. Next.

NYSE looks a lot better and navigates easily to `Data` -> `Real Time Data` -> `NYSE BBO`. The [pricing](https://www.nyse.com/publicdocs/nyse/data/NYSE_Market_Data_Pricing.pdf) is free for their “DataFeed” but the [specs](https://www.nyse.com/publicdocs/nyse/data/XDP_Common_Client_Specification_v2.1h.pdf) look too complicated for what we’re doing. Next.

What about Bloomberg? They’re known for selling expensive subscriptions to their “Bloomberg Terminals” which as far as I know is The Place for institutional professional traders. Perhaps they have a lightweight free API for Main Street traders. Unfortunately, it looks like they make you “[talk to a specialist](https://www.bloomberg.com/professional/product/market-data/)” aka salesperson. Nope.

The primary sources from exchanges and Bloomberg all seem to require either fees or complicated data ingestion formats, so we need to move on to hopefully more consumer-friendly secondary sources.

## Secondary Sources

Perusing the top Google search results for “realtime stock quotes” has [IEX Trading](https://iextrading.com/) showing up in various locations (Quora, blog posts, HN). Here’s their mission:

> Since day one, IEX has been committed to increasing fairness and transparency in capital markets. We want to change the relationship between Wall Street and Main Street by building trust, providing choice and helping companies put their investors first.

And importantly:

> IEX is the only exchange to provide free market data. We believe data should be widely accessible.

Damn. Too good to be true?

Their [API docs](https://iextrading.com/developer/docs/) easily gets us to `https://api.iextrading.com/1.0/stock/aapl/quote` which returns a nice JSON response:

```json
{
	"symbol": "AAPL",
	"companyName": "Apple Inc.",
	"latestPrice": 174.23,
	"changePercent": 0.00728,
	"marketCap": 821543234400,
	...
}
```

Hell yea.

~fin