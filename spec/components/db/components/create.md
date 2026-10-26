# create

Добавляет новую запись в таблицу БД

## Пример запроса

`INSERT INTO {table} ({columns}) VALUES ({parameters}) RETURNING {returnedColumns}`

`table` - `string`
`columns` - `string[]`
`parameters` - `Record<string, any>`
`returnedColumns` - `string[]`
