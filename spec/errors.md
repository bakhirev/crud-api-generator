# Ошибки

Формат ответа service см. [apps/service/index.md](apps/service/index.md).

Успешный вызов БД: `code` 200, `result` - `response` из [components/db/Connector.md](components/db/Connector.md).

Пустой `findAll`, `updateAll`, `removeAll`, `softRemoveAll` (ни одна строка не подошла под фильтр) - это успешный ответ.

## Коды

200 - успешный вызов БД
201 - аналог 200 для `create`
204 - аналог 200 для `findOne`, `findAll`, `updateAll`, если пустой массив
400 - ошибка валидации данных;
404 - неапознанный URL;
405 - правила для этого URL есть, для метода нет;
500 - общая внутренняя ошибка (например, падение запроса в БД)

HTTP при `code` >= 400 отдаёт `{ "message": result }`.
