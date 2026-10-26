# removeOne

Удаляет одну запись из таблицы БД

## Arguments

`id` - значение `primaryKey` нужной строки этой таблицы
`userReturnedColumns` - список колонок (`string[]`), необязательный

## Outputs

Результат запроса к БД. Коды ошибок см. `../../errors.md`

## Аргументы для вызова БД

`returnedColumns` список колонок из `table` (`string[]`)
- Если `executionSetting.returnedColumns` задан (не undefined), фильтруем список по нему.
- Если `userReturnedColumns` задан (не undefined), фильтруем список по нему.

`filters` пустой массив
- Если `context.executionSetting.forciblyFilters` задан (не undefined), добавляем их.
- Добавляем в фильтр `{ property: primaryKey, condition: "=", value: id }`. Если в `table.primaryKey` несколько значений, то и фильтров будет несколько, на каждое значение.

## Алгоритм работы

- `id` не задан, вернуть ошибку;
- подготовить аргументы;
- вызвать removeOne у БД;
