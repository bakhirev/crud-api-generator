# create

Добавляет новую запись в таблицу БД

## Arguments

`data` - обьект для добавления (`Record<string, any>`)
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

`columns` список колонок из `table` (`string[]`) соответствующих ключам в `parameters`

`returnedColumns` список колонок из `table` (`string[]`)
- Если `executionSetting.returnedColumns` задан (не undefined), фильтруем список по нему.
- Если `userReturnedColumns` задан (не undefined), фильтруем список по нему.

## Алгоритм работы

- `data` не задан или пустой объект, вернуть ошибку;
- подготовить аргументы;
- вызвать create у БД;
- результат первый элемент массива или null;
