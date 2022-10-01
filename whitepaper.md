---
title: Whitepaper
---
[Draft 2022.08.01]

### Abstract

The boom in cryptocurrency creates a tax filing challenge for retail crypto investors. Traditional financial institutions generate tax preparation forms at the end of the year, however, crypto exchanges are not able to do so because of limited coordination on their part. This loses investors' origin Cost Basis when assets are transferred cross-exchange, and presents a major reconciliation challenge at tax time.

In this paper, we introduce CoinTrail, a simple and effective algorithm for tracking Cost Basis and a Tax Calculation Engine which helps ease the mind of crypto HODLers.

### Introduction

Unlike existing Software as a Service products on the market, CoinTrail takes a local-first, app-based approach. It runs locally on the mobile device without the need for a backend, or even user signup. This ensures the privacy of the asset owner, and offers both a better user experience, and cheaper service. CoinTrail provides tax-calculation tools for three main use cases described below.

Tax calculation on the sale or transfer of a portion of an asset, a _tax-lot_, requires tracking of details such as date of original acquisition and price of the asset when it was obtained. CoinTrail automatically manages tax-lots when you make a trade or transfer between exchanges. Lots can be determined by one of several user-selected tax strategies. Cointrail shows which lot will be used prior to making a sale, which one will be reserved if you make a withdrawal, and tracks the Cost Basis of an asset that's transferred between exchanges.

With respect to lot calculation, clock skew across exchanges poses an issue, since the deduplication and tax lots management depends on matching withdraw/deposit transactions ordered in time. CoinTrail can handle skew which would otherwise report an overdraft when matching transactions.

The tax-implications of fees crypto exchanges charge is another tricky area to calculate correctly. Many exchanges don't show fees when doing a swap or convert from one crypto asset to another which leads to errors in calculating Cost Basis, lowering the tax deduction the investor withholds. CoinTrail addresses this problem by estimating fees using historical price discovery when permitted.

Finally, crypto hodlers typically keep some portion of their assets in cold storage such as a USB wallet. CoinTrail tracks reserve balances by automatically searching for withdrawals without corresponding deposits in other exchanges. Any non-payment withdrawal without a deposit will be treated as a reserve balance.

### Transactions

CoinTrail aggerates all transactions imported from CSV files or synced from Exchanges, Mining Pools or Wallets into a unified format, tracking the following actions:
- Earn
- Reward
- Sell
- Buy
- Mint
- Swap
- Deposit
- Withdraw

![Transactions](/assets/images/Transactions.png)

Transactions are automatically tagged with metadata such as #vendor or #source, then normalized, deduplicated and updated with Cost Basis using Historical Price Discovery from CoinGecko, Ftxus, and Coinbase.

### Tax Engine

CoinTrail supports 3 different tax strategies:
- Hifo (highest in first out)
- Fifo (first in first out)
- Filo (first in last out)

Lets take an example:

A user bought 1 BTC on [Coinbase](https://coinbase.com) at 35K and bought another 0.3 BTC for 36K. He then transfers 1 BTC to [CelsiusNetwork](https://celsius.network) to earn yield and 0.3 BTC to Cold Storage wallet. Few months later he then sold 0.5 BTC in [CelsiusNetwork](https://celsius.network) for USDC at 38K. Here is how the tax lots look for Hifo strategy:

![Hifo strategy](/assets/images/hifo-strategy-diagram.png)

[Sample.csv](/assets/downloads/whitepaper-sample.csv)

### Tax Planning

It's highly recommended to plan your crypto taxes in advance. With the help of CoinTrail, you can easily import CSV transactions or sync from exchanges, seeing your taxable income and realized gain/loss in one place.

![TaxLots](/assets/images/TaxLots.png)

### Tax Filing

To accommodate for all tax filing situations, although the default Genesis portfolio should be enough for 95% of the use cases. CoinTrail supports multiple tax portfolios concept for advance filing, depending on your needs.
- Taxable Income: if staking provider does not handle out 1099-MISC for Earn/Reward at year end then uses the amount that CoinTrail calculated when filing tax. If you have multiple staking providers and some does other don't, you should separate them out in different portfolio.
- Realized Gain/Loss: very straight forward to export tax form 8949 from CoinTrail and import into your favorite tax service.

![TaxFiling](/assets/images/TaxFiling.png)

### Conclusion

CoinTrail does not to have a central server for the app to harvest user information in order to protect user privacy. However, this also means that CoinTrail cannot collect any crash logs. This leads to challenges on app distribution, and supporting the user community.

Tax calculation is not as complex as one might think. It can be done manually with a small number of transactions but it's a challenge with many transactions over long periods of time. Many SaaS tax services take advantage and charge users with a high fee, and recurrencing subscriptions. CoinTrail takes an inexpensive yet powerful, privacy-first approach instead.

CoinTrail (beta) is available on iOS AppStore and being updated every 2 weeks with more Exchanges, Mining Pools, and Wallet integration.

### References

[1] https://www.irs.gov/pub/irs-drop/n-14-21.pdf

[2] https://turbotax.intuit.com/tax-tips/investments-and-taxes/your-cryptocurrency-tax-guide/L4k3xiFjB

[3] https://www.irs.gov/businesses/small-businesses-self-employed/self-employment-tax-social-security-and-medicare-taxes
