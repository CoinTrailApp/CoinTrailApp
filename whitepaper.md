[Draft 2022.04.01]

## Abstract

Booming in cryptocurrency creates tax filing challenge for individuals who own this asset class. Unlike, traditional finance where an institution can hand out 8949 tax form at the end of the year, the crypto exchanges are not able to do so due to lack of origin Cost Basic when assets being transferred cross exchanges.

In this paper, CoinTrail presents a very simple and effectively algorithm to keep track of Cost Basic and Tax Calculation Engine which helps easy the mind of crypto HODLers.

## Introduction

Unlike existing solutions on the market with SaaS based approach, CoinTrail is a Crypto Tax Calculator in your pocket. Just an app that runs locally on the mobile device, with no server, no backend, no signup...to ensure privacy of assets owner, offer a better user experience and cheaper service.

CoinTrail automatically manages tax-lots when you make a trade or transfer based on the tax strategy of your choice. It shows you which lot will be used prior to making a sale, which one will be reserved if you make a withdrawal and restore exact Cost Basic as deposit into other exchanges.

Fees is another mysterious thing when trading on exchanges. Many exchanges don't show fees when doing a swap or convert from one crypto asset to another. This leads to confusion when calculating Cost Basic, lowering tax deduction. CoinTrail addresses this problem by estimating fees using historical price discovery when permitted.

Off balance tracking is another cool feature. CoinTrail automatically matches all the withdrawals with deposits. For any withdrawal without a deposit will treat as off balance. This happens when transfering assets to a Cold Storage.

## Transactions

CoinTrail aggerates all transactions imported from CSV files or synced from Exchanges, Mining Pools or Wallets into a unify form format with basic actions:
- Earn
- Reward
- Sell
- Buy
- Swap
- Deposit
- Withdraw

Transactions are automatically tagged by #vendor, #source...normalized, deduplicated and corrected missing Cost Basic using Historical Price Discovery from CoinGecko, Ftxus and Coinbase.

[TBD]

## Tax Lots

CoinTrail supports 3 different tax strategies:
- Hifo (highest in first out)
- Fifo (first in first out)
- Filo (first in last out)

Let take an example:

A user bought 1 BTC on Coinbase at 35K and bought another 0.3 BTC for 36K. He then transfers 1 BTC to CelsiusNetwork to earn yield and 0.3 BTC to Cold Storage. Few months later he then sold 0.5 BTC on CelsiusNetwork for USDC at 38K. Here is how the tax lots look for each tax strategy.

![Hifo strategy](/assets/images/hifo-strategy-diagram.png)

## Import

[TBD]

## Sync

[TBD]

## Export

[TBD]

## Search

[TBD]

## Tax Filing

To accomodate for all tax filing situations, although the default Genesis portfolio should be enough for 95% of the use cases.  CoinTrail supports multiple tax portfolios concept for advance filing. Depends on your need:
- Taxable Income: if staking provider does not handle out 1099-MISC for Earn/Reward at year end then uses the amount that CoinTrail calculated when filing tax. If you have multiple staking providers and some does other don't, you should saperate them out in different portfolio.
- Realized Gain/Loss: very straight forward to export tax form 8949 from CoinTrail and import into your favorite tax service.

[TBD]

## Conclusion

Clock skew cross exchanges is a bit of an issue, since the deduplication and tax lots management are depends on it. A withdrawal transation happened in one exchange might record later than the deposit into other exchange. This's causing an overdraft when matching transaction.

To preserve privacy, CoinTrail chooses not to have a central server for the app to phone home, not collect any crash logs...This leads to some challanges on distribution and supporting the community.

Tax calculation is not that complex as one might think. It can be done manually with small number of transactions but gonna be a challange with larger transactions over long period of time. Many SaaS tax services take advatange and charge user a high fee, recurrence subscription... CoinTrail is nearly free, just here to help the community. CoinTrail (beta) is available on iOS AppStore and being update one in every 2 weeks, with more Exchanges, Mining Pools and Wallets integration.

## References

[1] https://www.irs.gov/pub/irs-drop/n-14-21.pdf

[2] https://turbotax.intuit.com/tax-tips/investments-and-taxes/your-cryptocurrency-tax-guide/L4k3xiFjB

[3] https://www.irs.gov/businesses/small-businesses-self-employed/self-employment-tax-social-security-and-medicare-taxes
