## 🛠 Connector Info

-   **Exchange Type**: Decentralized Exchange (DEX)
-   **Market Type**: Automatic Market Maker (AMM)

| Component                                        | Status    | Notes |
| ------------------------------------------------ | --------- | ----- |
| [2️⃣ AMM Connector](#2-amm-connector)             | ✅        |
| [3️⃣ Range AMM Connector](#3-range-amm-connector) | Not built |
| [🕯 AMM Data Feed](#amm-data-feed)                | ✅        |

## ℹ️ Exchange Info

-   **Website**: <https://www.splash.trade/>
-   **CoinMarketCap**: <https://coinmarketcap.com/exchanges/splash-trade/>
-   **CoinGecko**: <https://www.coingecko.com/en/exchanges/splash>

## 🔑 How to Connect

Generate a Maestro API key on : <https://www.gomaestro.org/>

Create a wallet on one of the supported networks below:

| Chain  | Networks  |
| ------ | --------- |
| `cardano` | `mainnet` |
| `cardano` | `testnet` |

From inside the Hummingbot client, run `gateway connect splash` in order to connect your wallet:

```
Which chain do you want splash to connect to? (cardano) >>>
Which network do you want splash to connect to? (mainnet) >>>
Enter your Maestro API key >>>
Do you want to continue to use node url 'https://mainnet.gomaestro-api.org/v1' for cardano-mainnet? (Yes/No) >>>
Enter your cardano-mainnet private key >>>
```

If connection is successful:

```
The splash connector now uses wallet [pubKey] on cardano-mainnet
```

## 2️⃣ AMM Connector

_Integration to this DEX's swap pricing and execution endpoints_

-   **ID**: `splash`
-   **Connection Type**: REST via [Gateway](/gateway)
-   **Folder**: <https://github.com/hummingbot/gateway/tree/main/src/connectors/splash>
-   **Default Configs**: <https://github.com/hummingbot/gateway/blob/main/src/templates/splash.yml>

### Endpoints

-   `/amm/price`
-   `/amm/trade`
-   `/amm/estimateGas`

For more info, run Gateway and go to <https:localhost:8080> in your browser to see detailed documentation for each endpoint.

## 🕯 AMM Data Feed

_Data feed of this exchange's real-time prices_

-   **ID**: `splash_[CHAIN]_[NETWORK]`
-   **Connection Type**: REST via [Gateway](/gateway)
-   **Folder**: <https://github.com/hummingbot/hummingbot/blob/master/hummingbot/data_feed/amm_gateway_data_feed.py>

### Usage

```python
from hummingbot.data_feed.amm_gateway_data_feed import AmmGatewayDataFeed
prices = AmmGatewayDataFeed(
        connector_chain_network="splash_cardano_mainnet",
        trading_pairs={"ADA-USDT", "ADA-rsERG"},
        order_amount_in_base=Decimal("1"),
    )
```