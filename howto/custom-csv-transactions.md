## Custom CSV Transactions

To fill in the gap of not yet supported exchanges or wallets, CoinTrail `2022.09.01` supports a flexible CSV transactions format. You can handcraft CSV files from trading activities and import to the app, for example of transactions in the [whitepaper](/whitepaper.html):

![Sample.csv](/assets/images/whitepaper-sample.png)

### CSV Format

Download [sample.csv](/assets/whitepaper-sample.csv) and use your favorite editor to prepare a transaction file with the same columns layout.

| Column       | Data Type   | Description | Example     |
|--------------|-------------|-------------|-------------|
| xId          | Int64       | for advanage usage, leave empty |             |
| Date         | Date        | `yyyy-MM-dd HH:mm:ss`, `yyyy-MM-dd HH:mm:ss zzz` |             |
| Action       | String      | `Earn`, `Reward`, `Sell`, `Buy`, `Swap`, `Withdraw`, `Deposit` |             |
| Asset        | String      |             | BTC         |
| Quantity     | Number      |             |             |
| Currency     | String      | Fiat currency or other asset, leave empty for auto lookup fiat|             |
| Total        | Number      | Net total `Buy = cost + fee, Sell = proceeds - fee` in Currency|             |
| Fee          | Number      | Fee in Currency|             |
| Tags         | String      | `Space delimited` for multiple tags, first tag always Vendor| Coinbase |
| Description  | String      |             |             |

### Advance example

The CSV format is flexible enough to support more complex transactions while maintaining the ease of use. Let looks at the sample below:

| xId | Date | Action | Asset | Quantity | Currency | Total | Fee | Tags | Description |
|-----|------|--------|-------|----------|----------|-------|-----|------|-------------|
|1|2021-05-26T20:11:57Z|Buy|BTC|0.00308108|USD|200|1.0||`Buy` BTC with known cost basic, `Currency = USD`|
|2|2021-06-26T20:11:57Z|Buy|BTC|0.00308108|||||`Buy` BTC with unknown cost basic, `Currency = empty`|
|3|2021-07-26T20:11:57Z|Buy|ETH|0.1||||||
|4|2021-07-27T20:11:57Z|Swap|ETH|0.2|SOL|20|0.5|Huobi|`Swap` ETH for SOL in single row, `Currency = SOL`|
| |2021-07-28T21:11:57Z|Sell|ETH|0.22||||Huobi||
| |2021-07-28T21:11:57Z|Buy|SOL|22||||Huobi||
|-100|2021-08-28T21:11:57Z|Swap|ATOM|163|USD|1500.12|30.45|Binance|`Swap` ATOM with known cost basic in 3 different rows, `negative xId` and `same Date`|
|-101|2021-08-28T21:11:57Z|Sell|ATOM|163|USD|1500.12|0|Binance||
|-102|2021-08-28T21:11:57Z|Buy|USDC|1500.12|USD|1500.12|0|Binance||
|-103|2021-09-28T21:11:57Z|Swap|ZUSD|1.7239|USD|1.7239||Binance|`Swap` ZUSD for ALGO|
|-104|2021-09-28T21:11:57Z|Sell|ZUSD|1.7239|USD|1.7239|0|Binance||
|-105|2021-09-28T21:11:57Z|Buy|ALGO|4.78753053|USD|1.7239|0.004|Binance||

- Using **xId** (negative or possitive) as hint during the import
- Using complex **Date** format: `yyyy-MM-dd'T'HH:mm:ss'Z'`, `yyyy-MM-dd'T'HH:mm:ss.SSS'Z'`, `yyyy-MM-dd'T'HH:mm:ss.SSSZ`, `MMMMM dd, yyyy h:mm a`
