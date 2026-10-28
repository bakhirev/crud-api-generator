# findOne

Находит один элемент в БД по primary key (id, uuid, code и т.п.)

## Arguments

`id` - значение `primaryKey` нужной строки этой таблицы

## Outputs

Результат запроса к БД

## Аргументы для вызова БД

`columns` список колонок из `table` (`string[]`);
- Если `executionSetting.returnedColumns` задан (не undefined), фильтруем список по нему.
- Если `userColumns` задан (не undefined), фильтруем список по нему.
- Возвращаем отфильтрованный `columns`

`filters`
- Если `userFilters` задан (не undefined), берем их.
    - Если `context.executionSetting.allowedFilters` задан (не undefined), фильтруем список по нему.
- Иначе `context.executionSetting.defaultFilters`
- Если `context.executionSetting.forciblyFilters` задан (не undefined), добавляем их.
- Добавляем в фильтры `{ property: primaryKey, condition: "=", value: id }`

## Алгоритм работы

- `id` не задан, вернуть ошибку;
- подготовить аргументы;
- вызвать findOne у БД;
- результат первый элемент массива или null;
