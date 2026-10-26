# updateOne

Обновляет одну запись в таблицу БД

## Arguments

`id` - значение `primaryKey` нужной строки этой таблицы
`data` - новые значения колонок (`Record<string, any>`)
`userReturnedColumns` - список колонок (`string[]`), необязательный

## Outputs

Результат запроса к БД

## Аргументы для вызова БД

`parameters` пустой обьект `Record<column, any>`
- Добавляем все значения из `executionSetting.defaultParameters`
- Добавляем все значения из `data` (с заменой).
    - Если `executionSetting.allowedParameters` задан (не undefined), фильтруем по нему (удаляем лишнее).
- Добавляем `executionSetting.forciblyParameters` (с заменой).
- Удаляем ключи, которые не являются колонками таблицы `table`.
- Вызываем валидацию (`validation.md`) по правилам `executionSetting.validationRules`. Если валидация вернула ошибку, возвращаем ошибку.

`returnedColumns` список колонок из `table` (`string[]`)
- Если `executionSetting.returnedColumns` задан (не undefined), фильтруем список по нему.
- Если `userReturnedColumns` задан (не undefined), фильтруем список по нему.

`filters` пустой массив
- Если `context.executionSetting.forciblyFilters` задан (не undefined), добавляем их.
- Добавляем в фильтр `{ property: primaryKey, condition: "=", value: id }`. Если в `table.primaryKey` несколько значений, то и фильтров будет несколько, на каждое значение.

## Алгоритм работы

- `id` не задан, вернуть ошибку;
- `data` не задан или пустой объект, вернуть ошибку;
- подготовить аргументы;
- вызвать updateOne у БД;
- результат первый элемент массива или null;
