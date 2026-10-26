# findAll

Находит все элементы в БД, которые соответствуют фильтрам поиска

## Arguments

`userFilters` - список фильтров (`FilterRule[]`), необязательный
`userColumns` - список колонок (`string[]`), необязательный
`userOrder` - порядок сортировки (`OrderRule[]`), необязательный
`userPagination` - пагинация (`PaginationRule`), необязательный

## Outputs

Результат запроса к БД

## Аргументы для вызова БД
  
`isAddTotalElements` = true

`columns` список колонок из `table` (`string[]`);
- Если `executionSetting.returnedColumns` задан (не undefined), фильтруем список по нему.
- Если `userColumns` задан (не undefined), фильтруем список по нему.
- Возвращаем отфильтрованный `columns`

`filters`
- Если `userFilters` задан (не undefined), берем их.
  - Если `context.executionSetting.allowedFilters` задан (не undefined), фильтруем список по нему.
- Иначе `context.executionSetting.defaultFilters`
- Если `context.executionSetting.forciblyFilters` задан (не undefined), добавляем их.

`order`
- Если `userOrder` задан (не undefined), берем их.
    - Если `context.executionSetting.allowedOrders` задан (не undefined), фильтруем список по нему.
- Иначе `context.executionSetting.defaultOrders`
- Если `context.executionSetting.forciblyOrders` задан (не undefined), добавляем их.

`pagination`
- Если `userPagination` задан (не undefined), берем её.
- Иначе `{ limit: 10, offset: 0 }`

## Алгоритм работы

- подготовить аргументы;
- вызвать findAll у БД;
