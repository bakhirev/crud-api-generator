# findAll

Находит все элементы в БД, которые соответствуют фильтрам поиска

## Дополнительные аргументы

`isAddTotalElements` - boolean;

## Пример запроса

`SELECT {columns}{totalElements} FROM {table} WHERE {filters} {order} {pagination}`

где:
- `columns` список колонок (`string[]`);
- `totalElements` = `isAddTotalElements` ? `, count (1) OVER () as total_elements` : '';
- `filters` см. `../getFiltersFromFilterRule.md`
- `order` см. `../getOrdersFromOrderRule.md`
- `pagination` см. `../getPaginationFromPaginationRule.md`
