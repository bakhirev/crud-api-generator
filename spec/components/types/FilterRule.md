# Формат описания фильтров (FilterRule)

## Правило фильтрации
```
{
  property?: string;
  condition: "=" | "!=" | ">" | "<" | ">=" | "<=" | "in" | "not-in" | "null" | "not_null";
  value?: any;
}
```

`property` — поле
`condition` — условие
`value` — значение

## Массив FilterRule

Массив может содержать только FilterRule или только массивы.
FilterRule внутри одного массива обрабатываются через И
FilterRule в двух сосдених массива обрабатываются через ИЛИ

Например:
```
[ a, b, c] -> a И b И c
[ [a, b], [c]] -> (a И b) ИЛИ c
[ [a, b], [[с], [d, e]]] -> (a И b) ИЛИ (c ИЛИ (d И e))
```

### Вложенные FilterRule

Поле value может содержать обьект, чтобы ссылаться на другие таблицы. Например:
```
{
  "property": "user_id",
  "condition": "in",
  "value": {
    "type": "subquery",
    "table": "orders",
    "property": "user_id",
    "filters": [
      { "property": "status", "condition": "=", "value": "completed" },
      { "property": "total", "condition": ">", "value": 1000 }
    ]
  }
}
```
#### type = "subquery"

`table` — имя связанной таблицы.
`property` — поле, которое нужно выбрать (по умолчанию id или первичный ключ).
`filters` — массив вложенных фильтров (опционально).

#### type = "union"

Используется, когда условие должно выполняться, если значение находится в одном из нескольких наборов данных.
```
{
  "property": "email",
  "condition": "in",
  "value": {
    "type": "union",
    "queries": [
      {
        "type": "subquery",
        "table": "subscribers",
        "property": "email",
        "filters": [ { "property": "active", "condition": "=", "value": true } ]
      },
      {
        "type": "subquery", 
        "table": "vip_users",
        "property": "email"
      }
    ]
  }
}
```

#### type = "sql"
```
{
  "property": "email",
  "condition": "in",
  "value": {
    "type": "sql",
    "sql": "SELECT email FROM users WHERE level > $1",
    "value": [1]
  }
}
```

`sql` — строка SQL (например, "ST_Distance(geo_point, ST_MakePoint($1, $2))").
`value` — массив значений для плейсхолдеров или первое значение.
