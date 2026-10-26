# removeOne

Удаляет одну запись из таблицы БД

## Пример запроса

`DELETE FROM {table} WHERE {filters} RETURNING {returnedColumns}`

`table` - `string`
`filters` см. `../getFiltersFromFilterRule.md`
`returnedColumns` - `string[]`
