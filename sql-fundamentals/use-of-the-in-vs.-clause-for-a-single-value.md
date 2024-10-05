---
description: >-
  Both the "IN" and "=" clauses, when comparing a single value, perform
  identically in SQL, resulting in the same execution plan.
---

# Use of the IN vs. = Clause for a Single Value

Both clauses, when used to compare a single value, are treated the same way by the SQL query optimizer. This means that there is no performance difference between the two.

**Example:**

```sql
explain select * from items t where t.category = 'ARMOR';
-- or
explain select * from items i where i.category in ('ARMOR');
```

Both commands above will result in the same execution plan, which uses the `=` comparison.
