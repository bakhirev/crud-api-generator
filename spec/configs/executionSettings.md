# Описание методов взаимодействия с таблицей (executionSettings)

В виде JSON списка настроек исполнения

## Список настроек исполнения

```
{
  [ID_метода]: {
    [ID_модификатора]: Параметры исполнения
  }
}
```
`table` название таблицы [A-Za-z_0-9]+
`ID_метода` совпадает с методом service: `findOne`, `findAll`, `create`, `updateOne`, `updateAll`, `removeOne`, `removeAll`, `softRemoveOne`, `softRemoveAll`

## Параметры исполнения

```
{
  validationRules: Правило валидации[],

  returnedColumns: string[],

  allowedParameters: string[],
  defaultParameters: Record<ID_колонки, any>,
  forciblyParameters: Record<ID_колонки, any>,

  allowedFilters: string[],
  defaultFilters: Список фильтров[],
  forciblyFilters: Список фильтров[],

  allowedOrders: string[],
  defaultOrders: Параметры сортировки[],
  forciblyOrders: Параметры сортировки[],
}
```

`validationRules` правила валидации, см. `../components/validation.md`. По умолчанию генерируются на основе колонки (проверка типа, обязательность, мин. и макс. значение)

`allowedParameters` список разрешенных параметров, с которыми можно взаимодействовать (подставлять в запрос БД).
`defaultParameters` параметры запроса по умолчанию в формате ключ-значение
`forciblyParameters` параметры запроса заданные принудительно в формате ключ-значение

`allowedFilters` список разрешенных фильтров полученных от пользователя, см. `../components/types/FilterRule.md` (`property[]`).
`defaultFilters` список фильтров по умолчанию, если пользователь их не задал, см. `../components/types/FilterRule.md`
`forciblyFilters` список принудительных фильтров, которые будут применены в независимости от того указали их или нет, см. `../components/types/FilterRule.md`

`allowedOrders` список разрешенных настроек сортировки полученных от пользователя, см. `../components/types/OrderRule.md` (`property[]`).
`defaultOrders` список настроек сортировки по умолчанию, если пользователь их не задал, см. `../components/types/OrderRule.md`
`forciblyOrders` список принудительных настроек сортировки, которые будут применены в независимости от того указали их или нет, см. `../components/types/OrderRule.md`

### Правила заполнения полей по умочанию:

`validationRules` генерируются на основе описания колонки (проверка типа, обязательность, мин. и макс. значение)
 - Если колонка id или order, то значение должно быть > 0

`allowedParameters` список всех колонок в таблице.
`defaultParameters` пустой обьект
`forciblyParameters` пустой обьект

`allowedFilters` список всех колонок в таблице.
`defaultFilters` пустой массив
`forciblyFilters` пустой массив

`allowedOrders` список всех колонок в таблице.
`defaultOrders`
 - Если в таблице есть order, то по нему DESC
 - Иначе если в таблице есть id, то по нему DESC
 - Иначе если в таблице есть дата обновления, то по ней DESC
 - Иначе если в таблице есть дата создания, то по ней DESC
 - Иначе пустой массив.
`forciblyOrders` пустой массив
