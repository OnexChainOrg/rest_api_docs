# Trade API

The Trade API provides endpoints for placing and managing orders.

## Place Order

Place a new order.

**Endpoint:** `POST /api/v1/order`

**Headers:**
- `x-api-key`: Your API key

**Permissions Required:**
- `enable_spot_trade`

**Request Body:**

```json
{
  "symbol": "BTC_USDT",
  "side": "BUY",
  "type": "LIMIT",
  "quantity": "1.00000000",
  "price": "40000.00000000"
}
```

**Parameters:**

| Name        | Type   | Required | Description                    |
|-------------|--------|----------|--------------------------------|
| symbol      | string | Yes      | Trading pair symbol (e.g., BTC_USDT) |
| side        | string | Yes      | Order side (BUY or SELL)       |
| type        | string | Yes      | Order type (LIMIT or MARKET)   |
| quantity    | string | Yes      | Order quantity                 |
| price       | string | No       | Order price (required for LIMIT orders) |

**Response:**

```json
{
  "statusCode": 200,
  "data": {
    "orderId": "1234567890",
    "symbol": "BTC_USDT",
    "status": "NEW",
    "side": "BUY",
    "type": "LIMIT",
    "price": "40000.00000000",
    "quantity": "1.00000000",
    "leaveQuantity": "0.00000000",
    "time": 1499827319559
  },
  "timestamp": "2024-03-21T10:00:00.000Z"
}
```

## Cancel Order

Cancel an existing order.

**Endpoint:** `DELETE /api/v1/order`

**Headers:**
- `x-api-key`: Your API key

**Permissions Required:**
- `enable_spot_trade`

**Request Body:**

```json
{
  "orderId": "1234567890"
}
```

**Parameters:**

| Name    | Type   | Required | Description                    |
|---------|--------|----------|--------------------------------|
| orderId | string | Yes      | Order ID to cancel             |

**Response:**

```json
{
  "statusCode": 200,
  "data": {
    "orderId": "1234567890",
    "symbol": "BTC_USDT",
    "price": 0.00152,
    "quantity": 100,
    "leaveQuantity": 100,
    "side": "Sell",
    "type": "Limit",
    "status": "cancelled",
    "timestamp": 1747637135399
  },
  "timestamp": "2024-03-21T10:00:00.000Z"
}
```

## Error Codes

Common error codes for trade endpoints:

- 400: Invalid request parameters
- 401: Invalid API key
- 403: Insufficient permissions
- 404: Order not found
- 429: Too many requests
- 500: Internal server error 