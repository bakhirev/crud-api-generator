# getFiltersFromFilterRule

На вход FilterRule[].
На выходе SQL.

Example:

```json
[
  { property: "id", condition: "in", value: [1, 2, 3, 4, 5] },
  { property: "name", condition: "=", value: "some" }
]
```

```sql
id IN (1, 2, 3, 4, 5) AND name = 'some'
```
