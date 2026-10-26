# findOne

Находит один элементы в БД, который соответствует фильтрам поиска

## Пример запроса

`SELECT {columns} FROM {table} WHERE {filters} LIMIT 1`

где:
- `columns` список колонок (`string[]`);
- `filters` см. `../getFiltersFromFilterRule.md`
