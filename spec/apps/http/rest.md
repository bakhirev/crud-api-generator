# REST

Протокол `rest` для [HTTP](index.md).
Адреса - [configs/http/rest.md](../../configs/http/rest.md). Если запрашиваемого адреса нет - 404
Ответ - JSON. Коды и тело ошибки - [errors.md](../../errors.md).


Тело `create`, `updateOne`, `updateAll` - объект колонок.
`findAll` берёт фильтры, сортировку и пагинацию из параметров запроса.
`updateAll`, `removeAll`, `softRemoveAll` берут `userFilters` из тела.
