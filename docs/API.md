# API Documentation

## Base URL
```
http://localhost:8080/api
```

## Endpoints

### 1. Health Check

**GET** `/health`

Check if the API is running.

**Response:**
```json
{
  "status": "healthy",
  "timestamp": "2026-01-06T10:00:00Z"
}
```

---

### 2. Summary Metrics

**GET** `/metrics/summary`

Get high-level business metrics for a specified period.

**Query Parameters:**
| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| period | string | No | 30d | Time period (7d, 30d, 90d, 1y) |

**Example Request:**
```bash
curl http://localhost:8080/api/metrics/summary?period=30d
```

**Response:**
```json
{
  "totalRevenue": 245680.00,
  "totalOrders": 1823,
  "avgOrderValue": 134.78,
  "conversionRate": 3.24,
  "activeProducts": 156,
  "lowStockItems": 12
}
```

---

### 3. Sales Trend

**GET** `/sales/trend`

Get sales trend data over time.

**Query Parameters:**
| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| interval | string | No | daily | Data interval (daily, weekly, monthly) |
| period | string | No | 30d | Time period |

**Example Request:**
```bash
curl http://localhost:8080/api/sales/trend?interval=daily&period=30d
```

**Response:**
```json
{
  "interval": "daily",
  "period": "30d",
  "data": [
    {
      "date": "2026-01-01",
      "revenue": 8520.00,
      "orders": 64
    },
    {
      "date": "2026-01-02",
      "revenue": 9340.00,
      "orders": 71
    }
  ]
}
```

---

### 4. Top Products

**GET** `/products/top`

Get top performing products.

**Query Parameters:**
| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| limit | integer | No | 10 | Number of products |
| sortBy | string | No | revenue | Sort criteria (revenue, units_sold) |
| period | string | No | 30d | Time period |

**Example Request:**
```bash
curl http://localhost:8080/api/products/top?limit=5&sortBy=revenue
```

**Response:**
```json
{
  "products": [
    {
      "productId": 123,
      "name": "Wireless Headphones",
      "category": "Electronics",
      "unitsSold": 342,
      "totalRevenue": 34200.00,
      "stockQuantity": 45
    }
  ],
  "count": 5
}
```

---

### 5. Inventory Alerts

**GET** `/inventory/alerts`

Get low stock and reorder alerts.

**Example Request:**
```bash
curl http://localhost:8080/api/inventory/alerts
```

**Response:**
```json
{
  "alerts": [
    {
      "productId": 456,
      "name": "Smart Watch",
      "stockQuantity": 8,
      "reorderLevel": 20,
      "alertType": "low_stock"
    },
    {
      "productId": 789,
      "name": "USB Cable",
      "stockQuantity": 0,
      "reorderLevel": 100,
      "alertType": "out_of_stock"
    }
  ],
  "total": 12
}
```

---

## Error Responses

### Format
```json
{
  "error": "Error message",
  "status": 400,
  "timestamp": "2026-01-06T10:00:00Z"
}
```

### Status Codes
| Code | Description |
|------|-------------|
| 200 | Success |
| 400 | Bad Request |
| 404 | Not Found |
| 500 | Internal Server Error |

---

## Rate Limiting

**Planned**: 100 requests per minute per IP address

## Authentication

**Planned**: JWT token-based authentication

---

**Last Updated**: January 2026  
**Documentation Status**: In Progress




Java, Spring Boot, React, MySQL, Redis
GitHub: github.com/yourusername/ecommerce-analytics-dashboard
        ↑ 改成你的实际username
