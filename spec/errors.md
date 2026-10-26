# Ошибки

Формат ответа service см. [components/service/index.md](components/service/index.md).

Успешный вызов БД: `code` 200, `result` — `response` из [components/db/Connector.md](components/db/Connector.md).

Пустой `findAll`, `updateAll`, `removeAll`, `softRemoveAll` (ни одна строка не подошла под фильтр) — это успешный ответ.

## Коды

| Ситуация | code | result |
| --- | --- | --- |
| `id` не задан | 400 | `id не задан` |
| `data` не задан или пустой объект | 400 | `data не задан` |
| `userFilters` не задан или пустой массив | 400 | `userFilters не задан` |
| `parameters` пустой (`softRemoveOne`, `softRemoveAll`) | 400 | `parameters не задан` |
| валидация вернула непустую строку | 400 | эта строка |
| `findOne`, `updateOne`, `removeOne`, `softRemoveOne`: запрос успешен, строк нет | 404 | `Запись не найдена` |
| `DBConnector.query` вернул `status: false` | 500 | `errorMessage` |

HTTP при `code` 400, 404 или 500 отдаёт `{ "message": result }`.
