# WebSocket API

The OnexChain WebSocket API provides real-time market data and user data streams.

## WebSocket Connection

**WebSocket URL:** `/stream?streams=streamName1/streamName2/...`

<!-- ## Authentication

For private data streams, you need to authenticate using your API key. Include the API key in the connection URL:

```
wss://api.onexchain.com/ws?apiKey=YOUR_API_KEY
``` -->

## Market Data Streams

### Order Book Stream

Subscribe to order book updates for a symbol.

**Stream Name:** `{symbol}@depth`

<!-- **Example:**
```json
{
  "method": "SUBSCRIBE",
  "params": ["btc_usdt@depth"],
  "id": 1
}
``` -->

**Response:**
```json
{
  "lastUpdatedId": "2025-05-19T07:07:11.029Z",
  "asks": [
      [
          "0.00152000",
          "100.00000000"
      ],
      [
          "0.00153000",
          "300.00000000"
      ]
  ],
  "bids": [
      [
          "0.00151000",
          "300.00000000"
      ]
  ]
}
```

<!-- ### Trade Stream

Subscribe to real-time trade updates for a symbol.

**Stream Name:** `{symbol}@trade`

**Response:**
```json
{
  "stream": "btc_usdt@trade",
  "data": {
    "e": "trade",
    "E": 1499405658658,
    "s": "BTC_USDT",
    "t": 12345,
    "p": "0.0015",
    "q": "100",
    "b": 88,
    "a": 50,
    "T": 1499405658657,
    "m": true
  }
}
``` -->

### Kline/Candlestick Stream

Subscribe to candlestick updates for a symbol.

**Stream Name:** `{symbol}@kline_{interval}`

**Kline Intervals**
- `1m`: 1 minute
- `5m`: 5 minutes
- `15m`: 15 minutes
- `30m`: 30 minutes
- `1h`: 1 hour
- `2h`: 2 hours
- `4h`: 4 hours
- `1d`: 1 day
- `1w`: 1 week
- `1M`: 1 month



<!-- **Example:**
```json
{
  "method": "SUBSCRIBE",
  "params": ["btc_usdt@kline_1m"],
  "id": 1
}
``` -->

**Response:**
```json
{
    "e": "kline",
    "E": 1747638388444,
    "s": "SOL_BTC",
    "k": {
        "h": 0.00152,
        "l": 0.0015,
        "q": 1.812,
        "o": 0.00152,
        "c": 0.0015,
        "n": 6,
        "t": 1747638388425,
        "T": 1747638007623,
        "i": "1d",
        "s": "SOL_BTC",
        "B": "0"
    }
}
```

<!-- ## User Data Stream

Subscribe to user data updates (orders, trades, etc.).

**Stream Name:** `user`

**Example:**
```json
{
  "method": "SUBSCRIBE",
  "params": ["user"],
  "id": 1
}
```

**Response:**
```json
{
  "stream": "user",
  "data": {
    "e": "executionReport",
    "E": 1499405658658,
    "s": "BTC_USDT",
    "c": "100000",
    "S": "BUY",
    "o": "LIMIT",
    "f": "GTC",
    "q": "1.00000000",
    "p": "0.10200000",
    "P": "0.00000000",
    "F": "0.00000000",
    "g": -1,
    "C": "",
    "x": "NEW",
    "X": "NEW",
    "r": "NONE",
    "i": 4293153,
    "l": "0.00000000",
    "z": "0.00000000",
    "L": "0.00000000",
    "n": "0",
    "N": null,
    "T": 1499405658657,
    "t": -1,
    "I": 8641984,
    "w": true,
    "m": false,
    "M": false,
    "O": 1499405658657,
    "Z": "0.00000000",
    "Y": "0.00000000"
  }
}
``` -->

<!-- 
## WebSocket Commands

### Subscribe

Subscribe to one or more streams.

```json
{
  "method": "SUBSCRIBE",
  "params": ["btc_usdt@depth", "btc_usdt@trade"],
  "id": 1
}
```

### Unsubscribe

Unsubscribe from one or more streams.

```json
{
  "method": "UNSUBSCRIBE",
  "params": ["btc_usdt@depth"],
  "id": 1
}
```

### List Subscriptions

List all current subscriptions.

```json
{
  "method": "LIST_SUBSCRIPTIONS",
  "id": 1
}
```

## Error Handling

WebSocket errors are returned in this format:

```json
{
  "code": 1000,
  "msg": "Invalid request",
  "id": 1
}
```

Common error codes:
- 1000: Invalid request
- 1001: Invalid API key
- 1002: Rate limit exceeded
- 1003: Invalid symbol
- 1004: Invalid interval
- 1005: Invalid stream name  -->