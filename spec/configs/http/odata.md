# Правила описания OData адресов

Все тоже самое что в `rest.md`

Файл, уровни и поле `method` не меняются. Меняются пути, глаголы и разбор запроса. Это правила обработчика `odata`, не вторая схема.

```json
{
  "/testAccessGroup": {
    "get": { "method": "findAll" },
    "post": { "method": "create" }
  },
  "/testAccessGroup(id={id})": {
    "get": { "method": "findOne" },
    "patch": { "method": "updateOne" },
    "delete": { "method": "removeOne" }
  },
  "/testAccessGroup(id={id})/softRemoveOne": {
    "post": { "method": "softRemoveOne" }
  },
  "/testAccessGroup/updateAll": { "post": { "method": "updateAll" } },
  "/testAccessGroup/removeAll": { "post": { "method": "removeAll" } },
  "/testAccessGroup/softRemoveAll": { "post": { "method": "softRemoveAll" } }
}
```

Путь ключа — один сегмент `имя(колонка={колонка},...)`. Имена колонок и порядок — из `primaryKey`. Сегмент `{id}` между слэшами для OData не используется: клиент так не ходит.

`updateAll`, `removeAll`, `softRemoveAll` — связанные действия, всегда POST. `softRemoveOne` висит на экземпляре, потому что DELETE уже занят `removeOne`. Частичное обновление — PATCH, PUT в каталог не ставится.

Префикс `/odata` выбирает протокол и в файл не пишется. Методы сервиса те же, что у REST: `findAll`, `findOne`, `create`, `updateOne`, `updateAll`, `removeOne`, `removeAll`, `softRemoveOne`, `softRemoveAll`.

## Запрос

Запрос переводится в те же параметры, что уже ест сервис:

| OData | Параметр сервиса |
| --- | --- |
| `$filter` | `userFilters` |
| `$select` | `userColumns` |
| `$orderby` | `userOrder` |
| `$top` | `userPagination.limit` |
| `$skip` | `userPagination.offset` |
| тело POST/PATCH | колонки записи и `userReturnedColumns` |

`$expand`, `$search`, `$apply` и пакет `$batch` в эту карту не входят.

## Служебные ресурсы

`$metadata` и документ сервиса собираются из `table.json`, в `http.json` их нет.

## Ответ

Ответ коллекции — `{ "@odata.context", "value" }`. Ответ одной записи — объект без конверта `value`.
