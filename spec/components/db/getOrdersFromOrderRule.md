# getOrdersFromOrderRule

На вход OrderRule[].
На выходе SQL.

Example:
```json
[
  {
    "property": "city",
    "direction": "ASC"
  },
  {
    "property": "last_name",
    "direction": "DESC"
  }
]
```

```sql
ORDER BY city ASC, last_name DESC;
```

