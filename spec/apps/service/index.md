# Класс Service

Обертка для подготовки и валидации данных перед работой с БД

## Структуры данных

### Конструктор

`table` - описание таблицы в БД (см. `tables.md`)
`executionSettings` - описание методов взаимодействия с таблицей (см. `executionSettings.md`)
`db` - данные подключенных баз данных

### Return value
```
{
  code: number
  result: any
}
```

`code` - http-код результата. Коды ошибок см. `../../errors.md`
`result` - сообщение об ошибке или результат выполнения запроса к БД (json)

## Методы

Реализация каждого метода вынесена в отдельный файл.

Последние два аргумента любого метода:
`context` - см. `context.md`  
`methodName[]` - см. `executionSettings.md`  

В начале каждого метода вызывается `./getExecutionSetting.md`

## Структура кода`

service
  [methodName] (get|search|update|remove|...)
    
    plugins.apply("service-before-validate", context);
    validate params
    plugins.apply("service-after-validate", context);

    plugins.apply("service-before-db-query", context);
    db
      pg
        [methodName] (get|search|update|remove|...)
      mySql
      ...
    plugins.apply("service-after-db-query", context);

    any logic
