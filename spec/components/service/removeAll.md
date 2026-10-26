# removeAll

Аналог removeOne, но удаляет несколько записей в таблице БД

## Arguments

`userFilters` - список фильтров (`FilterRule[]`)

## Outputs

Результат запроса к БД. Коды ошибок см. `../../errors.md`

## Аргументы для вызова БД

см `./removeOne`

`filters`
- Если `userFilters` задан (не undefined), берем их.
    - Если `context.executionSetting.allowedFilters` задан (не undefined), фильтруем список по нему.
- Иначе `context.executionSetting.defaultFilters`
- Если `context.executionSetting.forciblyFilters` задан (не undefined), добавляем их.

## Алгоритм работы

- `userFilters` не задан или пустой массив, вернуть ошибку;
- подготовить аргументы;
- вызвать removeAll у БД;
