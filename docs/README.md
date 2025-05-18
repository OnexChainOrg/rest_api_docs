# OnexChain API Documentation

Welcome to the OnexChain API documentation. This documentation provides detailed information about the REST API and WebSocket API endpoints available in the OnexChain platform.

## Table of Contents

[filename](_sidebar.md ':include')


## Base URL

All REST API endpoints are prefixed with `/api/v1/`

## Authentication

Most endpoints require API key authentication. See the [Authentication](./authentication.md) section for more details.

<!-- ## Rate Limits

API requests are subject to rate limiting. The specific limits are documented in each endpoint's description. -->
<!-- 
## Response Format

All responses follow this format:

```json
{
  "statusCode": 200,
  "data": {
    // Response data
  },
  "timestamp": "2024-03-21T10:00:00.000Z",
  "message": "Success"
}
``` -->

## Error Codes

Common error codes:

- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 429: Too Many Requests
- 500: Internal Server Error

## WebSocket API

For real-time data, please refer to the [WebSocket API](./WebSocket/Readme.md) documentation. 