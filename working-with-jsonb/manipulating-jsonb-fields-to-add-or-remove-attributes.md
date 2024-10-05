---
description: >-
  Use the || operator to add attributes and the - operator to remove them from
  JSONB fields in SQL queries.
---

# Manipulating JSONB Fields to Add or Remove Attributes

The examples below are demonstrated using `SELECT`, but the operations can be applied anywhere, such as updating a record with `UPDATE`.\
\


#### **Adding Attributes**

To add new attributes to an existing JSONB field, we can use the `||` operator, which functions as a concatenation operator for JSON.

**Example:**

```sql
SELECT 
    a.metadata || ('{"DVD": "ROM"}') AS metadata_new_attribute,
    a.* 
FROM audit a;
```

_Note_: The `||` operator is equivalent to `CONCAT`, and can be used to add multiple attributes at once.\


#### **Removing Attributes**

To remove one or more attributes from a JSONB field, we use the `-` operator.

**Example:**

```sql
SELECT 
    a.metadata - 'amount' AS metadata_without_amount,
    a.* 
FROM audit a;
```
