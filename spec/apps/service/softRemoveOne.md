# softRemoveOne

Помечает одну запись удалённой. Признак удаления - `forciblyParameters` этого метода (например `deleted_at` или `is_deleted`).

## Arguments

`id` - значение `primaryKey` нужной строки этой таблицы
`userReturnedColumns` - список колонок (`string[]`), необязательный

## Outputs

Результат запроса к БД. Коды ошибок см. `../../errors.md`

## Аргументы для вызова БД

`parameters` пустой обьект `Record<column, any>`
- Добавляем все значения из `executionSetting.defaultParameters`
- Добавляем `executionSetting.forciblyParameters` (с заменой).
- Удаляем ключи, которые не являются колонками таблицы `table`.

`returnedColumns` список колонок из `table` (`string[]`)
- Если `executionSetting.returnedColumns` задан (не undefined), фильтруем список по нему.
- Если `userReturnedColumns` задан (не undefined), фильтруем список по нему.

`filters` пустой массив
- Если `context.executionSetting.forciblyFilters` задан (не undefined), добавляем их.
- Добавляем в фильтр `{ property: primaryKey, condition: "=", value: id }`. Если в `table.primaryKey` несколько значений, то и фильтров будет несколько, на каждое значение.

## Алгоритм работы

- `id` не задан, вернуть ошибку;
- подготовить аргументы;
- `parameters` пустой, вернуть ошибку;
- вызвать updateOne у БД;
