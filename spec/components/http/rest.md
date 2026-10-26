# REST

Протокол `rest` для [HTTP](index.md). Адреса — [configs/http/rest.md](../../configs/http/rest.md). Ответ — JSON. Коды и тело ошибки — [errors.md](../../errors.md).

## Методы по умолчанию

| HTTP | URL | service |
| --- | --- | --- |
| GET | `/{table}` | `findAll` |
| POST | `/{table}` | `create` |
| GET | `/{table}/{primaryKey}` | `findOne` |
| PUT | `/{table}/{primaryKey}` | `updateOne` |
| DELETE | `/{table}/{primaryKey}` | `removeOne` |
| POST | `/{table}/{primaryKey}` | `softRemoveOne` |
| POST | `/{table}/updateAll` | `updateAll` |
| POST | `/{table}/removeAll` | `removeAll` |
| POST | `/{table}/softRemoveAll` | `softRemoveAll` |

`primaryKey` в пути — значение ключа. `updateAll`, `removeAll`, `softRemoveAll` — фиксированные имена методов, не значения ключа.

Тело `create`, `updateOne`, `updateAll` — объект колонок. `findAll` берёт фильтры, сортировку и пагинацию из параметров запроса. `updateAll`, `removeAll`, `softRemoveAll` берут `userFilters` из тела.
