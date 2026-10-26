# Сканер BD

Подключается к БД. Смотрит какие таблицы в ней есть. Сохраняет JSON файлы с описанием.

## Параметры

На входе ожидает
- обьект данных для подключения к БД (использует `dbConnector`). Формат см. `../../configs/db.md`. По умолчанию искать в `../configs/db.json`
- путь, по которому сохранить файл (по умолчанию `../configs/`)

## Алгоритм работы

Для каждой таблицы в каталоге `[имя базы]/[имя таблицы]/` сохранить `table.json` и `executionSettings.json` по `../../configs/index.md`.

Один `http.json` в корне каталога сохранения (по умолчанию `../configs/http.json`). В нём маршруты всех таблиц, формат см. `../../configs/http/index.md`, методы по умолчанию см. `../../components/http/rest.md`.
Сегмент таблицы в URL — `format(имя таблицы, "camelCase")`, см. `../../components/formatter.md`. Пустой результат — маршруты этой таблицы не добавлять.
Колонки `primaryKey` попадают в путь как `{имя колонки}` в порядке списка. Пустой `primaryKey` — маршруты с ключом не добавлять.
`updateAll`, `removeAll`, `softRemoveAll` в пути остаются как есть.

Таблица `test_users` с `primaryKey` `["id"]`:

```
{
  "/testUsers": {
    "get": { "method": "findAll" },
    "post": { "method": "create" }
  },
  "/testUsers/{id}": {
    "get": { "method": "findOne" },
    "put": { "method": "updateOne" },
    "delete": { "method": "removeOne" },
    "post": { "method": "softRemoveOne" }
  },
  "/testUsers/updateAll": { "post": { "method": "updateAll" } },
  "/testUsers/removeAll": { "post": { "method": "removeAll" } },
  "/testUsers/softRemoveAll": { "post": { "method": "softRemoveAll" } }
}
```