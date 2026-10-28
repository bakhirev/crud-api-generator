# updateAll

Аналог updateOne, но обновляет несколько записей в таблице БД

## Arguments

`userFilters` - список фильтров (`FilterRule[]`)
`data` - обьект для добавления (`Record<string, any>`)

## Outputs

Результат запроса к БД

## Аргументы для вызова БД

см `./updateOne`

`filters`
- Если `userFilters` задан (не undefined), берем их.
    - Если `context.executionSetting.allowedFilters` задан (не undefined), фильтруем список по нему.
- Иначе `context.executionSetting.defaultFilters`
- Если `context.executionSetting.forciblyFilters` задан (не undefined), добавляем их.

## Алгоритм работы

- `userFilters` не задан или пустой массив, вернуть ошибку;
- `data` не задан или пустой объект, вернуть ошибку;
- подготовить аргументы;
- вызвать updateAll у БД;
