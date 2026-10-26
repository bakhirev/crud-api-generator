# updateOne

Обновляет одну запись в таблицу БД

## Пример запроса

`UPDATE {table} SET ({parameters}) WHERE {filters} RETURNING {returnedColumns}`

`table` - `string`
`parameters` - `Record<string, any>`
`filters` см. `../getFiltersFromFilterRule.md`
`returnedColumns` - `string[]`
