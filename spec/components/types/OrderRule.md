# Формат описания сортировки (OrderRule)

## Правило сортировки
```
{
  "property": string,
  "direction": "ASC" | "DESC",
}
```

`property` поле, по которому сортируют
`direction` направление сортировки

## Список правил сортировки

Example:

```
[
  {
    "property": "level",
    "direction": "ASC"
  },
  {
    "property": "create_at",
    "direction": "DESC"
  }
]
```

