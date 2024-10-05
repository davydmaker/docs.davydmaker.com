---
description: >-
  Use jsonb_each_text() to expand JSONB fields into key-value rows, simplifying
  data analysis and manipulation in PostgreSQL.
---

# Manipulating JSONB with jsonb\_each\_text() to Expand Fields

The PostgreSQL function `jsonb_each_text()` is a powerful tool that transforms elements of a JSONB object into separate key-value rows, making data analysis and manipulation easier.

**Practical Example**: Suppose you want to analyze order details stored in a JSONB column, which includes information such as purchased items, quantities, and order status.

```sql
-- Expanding JSONB to view key and value
SELECT key, value
FROM orders o,
LATERAL jsonb_each_text(o.details)
WHERE o.order_id = '12345';

-- Filtering and ordering the order status history
SELECT
    o.order_id,
    key,
    value,
    o.created_at
FROM orders o,
LATERAL jsonb_each_text(o.details)
WHERE
    o.order_id = '12345' AND
    key = 'status'
ORDER BY o.created_at DESC;
```

***
