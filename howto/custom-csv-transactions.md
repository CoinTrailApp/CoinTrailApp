## Custom CSV Transactions

To fill in the gap of not yet supported exchanges or wallets, CoinTrail 2022.09.01 supports a flexible CSV transactions format. You can handcraft CSV files from trading activities and import to the app, for example of transactions in the [whitepaper](/whitepaper.html):

![Sample.csv](/assets/images/whitepaper-sample.png)

### CSV Format

Download [sample.csv](/assets/whitepaper-sample.csv) and use your favorite editor to prepare a transaction file with the same columns layout.

| Column       | Data Type   | Description | Example     |
---------------|-------------|-------------|--------------
| xId          | Int64       | for advanage useage, leave empty |             |
| Date         | Date        | in format of "yyyy-MM-dd HH:mm:ss" or "yyyy-MM-dd HH:mm:ss zzz" |             |
| Action       | String      | Earn, Reward, Sell, Buy, Swap, Withdraw, Deposit, Fee |             |
| Asset        | String      |             | BTC, ETH... |
| Quantity     | Number      |             |             |
| Currency     | String      | Fiat currency or other asset, leave empty for auto lookup fiat|             |
| Total        | Number      | Net total in Currency|             |
| Fee          | Number      | Fee in Currency|             |
| Tags         | String      | Space delimited for multiple tags, first tag always Vendor| Coinbase |
| Description  | String      |             |             |

### Advance usage

- Automatically lookup cost basic
- Swapping assets
- DeFi/NFT
