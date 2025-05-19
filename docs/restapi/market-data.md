# Market Data API

The Market Data API provides endpoints for retrieving market data such as order books, candlestick data, recent trades, and price information.

## Order Book

Get the order book for a symbol.

**Endpoint:** `GET /api/v1/market/depth`

**Parameters:**

| Name  | Type   | Required | Description                    |
|-------|--------|----------|--------------------------------|
| symbol| string | Yes      | Trading pair symbol (e.g., BTC_USDT) |
| limit | number | No       | Default 100; max 1000          |

**Response:**

```json
{
  "statusCode": 200,
  "data": {
    "lastUpdateId": 1027024,
    "bids": [
      ["4.00000000", "431.00000000"]
    ],
    "asks": [
      ["4.00000200", "12.00000000"]
    ]
  },
  "timestamp": "2024-03-21T10:00:00.000Z"
}
```

## Kline/Candlestick Data

Get kline/candlestick data for a symbol.

**Endpoint:** `GET /api/v1/market/klines`

**Parameters:**

| Name    | Type   | Required | Description                    |
|---------|--------|----------|--------------------------------|
| symbol  | string | Yes      | Trading pair symbol (e.g., BTC_USDT) |
| interval| string | Yes      | Kline interval (e.g., 1m, 5m, 1h, 1d) |
| limit   | number | No       | Default 500; max 1000          |
| from| number | No      | Start time in milliseconds     |
| to | number | No       | End time in milliseconds       |

**Response:**

```json
{
  "statusCode": 200,
  "data": [
    [
      1499040000000,      // Open time
      "0.01634790",       // Open
      "0.80000000",       // High
      "0.01575800",       // Low
      "0.01577100",       // Close
      "148976.11427815",  // Volume
      1499644799999,      // Close time
      "2434.19055334",    // Quote asset volume
      308,                // Number of trades
      "1756.87402397",    // Taker buy base asset volume
      "28.46694368",      // Taker buy quote asset volume
      "0"                 // Ignore
    ]
  ],
  "timestamp": "2024-03-21T10:00:00.000Z"
}
```

## Recent Trades

Get recent trades for a symbol.

**Endpoint:** `GET /api/v1/market/trades`

**Response:**

```json
{
  "statusCode": 200,
  "data": [
    {
      "id": "6829d46629c83b51de204a2b",
      "price": "0.00152000",
      "quoteQuantity": "0.01520000",
      "quantity": "10.00000000",
      "time": "2025-05-18T12:36:54.064Z"
    }
  ],
  "timestamp": "2024-03-21T10:00:00.000Z"
}
```

## Price Ticker

Get the current price for one or multiple symbols.

**Endpoint:** `GET /api/v1/market/price-ticker`

**Parameters:**

| Name   | Type   | Required | Description                    |
|--------|--------|----------|--------------------------------|
| symbols| string | Yes      | Multiple parameters, one for each symbol (e.g., symbols=BTC_USDT&symbols=ETH_USDT) |

**Response:**

```json
{
  "statusCode": 200,
  "data": [
    {
      "symbol": "BTC_USDT",
      "price": "40000.00"
    },
    {
      "symbol": "ETH_USDT",
      "price": "2000.00"
    }
  ],
  "timestamp": "2024-03-21T10:00:00.000Z"
}
```

## Last Transaction Price

Get the last transaction price for a symbol.

**Endpoint:** `GET /api/v1/market/market-price`

**Parameters:**

| Name  | Type   | Required | Description                    |
|-------|--------|----------|--------------------------------|
| symbol| string | Yes      | Trading pair symbol (e.g., BTC_USDT) |

**Response:**

```json
{
  "statusCode": 200,
  "data": {
    "symbol": "BTC_USDT",
    "price": "40000.00"
  },
  "timestamp": "2024-03-21T10:00:00.000Z"
}
``` 