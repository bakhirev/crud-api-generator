# Спецификация

Контракт модулей. Реализация - `nodejs/`.

Запрос идёт так: `http` → `getRequestParameters` → `service` → `db` → `sendResponse`.

## Конфиги

- [configs/index.md](configs/index.md) - каталог JSON
- [configs/db.md](configs/db.md) - подключение к БД
- [configs/tables.md](configs/tables.md) - описание таблицы
- [configs/executionSettings.md](configs/executionSettings.md) - настройки методов
- [configs/http/index.md](configs/http/index.md) - карта URL
- [configs/http/rest.md](configs/http/rest.md) - правила REST-адресов

## Общее

- [errors.md](errors.md) - коды и тело ошибки
- [components/context.md](components/context.md)
- [components/jsonFile.md](components/jsonFile.md)
- [components/formatter.md](components/formatter.md)
- [components/validation.md](components/validation.md)
- [components/validationErrorMessage.md](components/validationErrorMessage.md)
- [components/types/FilterRule.md](components/types/FilterRule.md)
- [components/types/OrderRule.md](components/types/OrderRule.md)
- [components/types/PaginationRule.md](components/types/PaginationRule.md)

## Service

- [apps/service/index.md](apps/service/index.md)
- [apps/service/getExecutionSetting.md](apps/service/getExecutionSetting.md)
- [apps/service/findOne.md](apps/service/findOne.md)
- [apps/service/findAll.md](apps/service/findAll.md)
- [apps/service/create.md](apps/service/create.md)
- [apps/service/updateOne.md](apps/service/updateOne.md)
- [apps/service/updateAll.md](apps/service/updateAll.md)
- [apps/service/removeOne.md](apps/service/removeOne.md)
- [apps/service/removeAll.md](apps/service/removeAll.md)
- [apps/service/softRemoveOne.md](apps/service/softRemoveOne.md)
- [apps/service/softRemoveAll.md](apps/service/softRemoveAll.md)

## DB

- [components/db/Connector.md](components/db/Connector.md)
- [components/db/components/index.md](components/db/components/index.md)
- [components/db/components/findOne.md](components/db/components/findOne.md)
- [components/db/components/findAll.md](components/db/components/findAll.md)
- [components/db/components/create.md](components/db/components/create.md)
- [components/db/components/updateOne.md](components/db/components/updateOne.md)
- [components/db/components/updateAll.md](components/db/components/updateAll.md)
- [components/db/components/removeOne.md](components/db/components/removeOne.md)
- [components/db/components/removeAll.md](components/db/components/removeAll.md)
- [components/db/getFiltersFromFilterRule.md](components/db/getFiltersFromFilterRule.md)
- [components/db/getOrdersFromOrderRule.md](components/db/getOrdersFromOrderRule.md)
- [components/db/getPaginationFromPaginationRule.md](components/db/getPaginationFromPaginationRule.md)

`softRemoveOne` и `softRemoveAll` вызывают `updateOne` и `updateAll`.

## HTTP

- [components/http/index.md](components/http/index.md)
- [components/http/rest.md](components/http/rest.md)
- [components/http/getRequestParameters/index.md](components/http/getRequestParameters/index.md)
- [components/http/sendResponse/index.md](components/http/sendResponse/index.md)
- [components/getRequestParameters/index.md](components/getRequestParameters/index.md)
- [components/sendResponse/index.md](components/sendResponse/index.md)

## Apps

- [apps/parser/dbServer.md](apps/parser/dbServer.md)
