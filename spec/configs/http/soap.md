# SOAP — `soap.json`

Один POST на таблицу. Операцию выбирает не глагол, а имя в конверте. Ключ первичного ключа в URL не входит: он лежит в теле операции, как в REST `{id}` лежит в пути.

```json
{
  "/testAccessGroup": {
    "findAll": { "method": "findAll" },
    "findOne": { "method": "findOne" },
    "create": { "method": "create" },
    "updateOne": { "method": "updateOne" },
    "removeOne": { "method": "removeOne" },
    "softRemoveOne": { "method": "softRemoveOne" },
    "updateAll": { "method": "updateAll" },
    "removeAll": { "method": "removeAll" },
    "softRemoveAll": { "method": "softRemoveAll" }
  }
}
```

| | |
| --- | --- |
| Файл | `configs/soap.json`, рядом с `http.json` |
| Ключ верхнего уровня | путь ресурса, тот же первый сегмент, что у REST: `/testAccessGroup` |
| Ключ второго уровня | имя операции. По умолчанию совпадает с `method`. Если имя на проводе другое, ключ — имя на проводе, `method` — метод сервиса |
| Значение | только `{ "method": "..." }`, как в `http.json` |
| URL | `POST /soap/testAccessGroup` |
| Версия | SOAP 1.1 (`text/xml`) и 1.2 (`application/soap+xml`), document/literal, обёрнутый стиль |

Методы сервиса те же, что у REST: `findAll`, `findOne`, `create`, `updateOne`, `updateAll`, `removeOne`, `removeAll`, `softRemoveOne`, `softRemoveAll`.

Префикс `/soap` выбирает протокол и в файл не пишется.

## Выбор операции

Имя операции берётся по порядку, первое непустое:

1. SOAP 1.1: заголовок `SOAPAction`, без кавычек. Если в значении есть `/`, берётся последний сегмент.
2. SOAP 1.2: параметр `action` у `Content-Type`, тот же последний сегмент.
3. Локальное имя первого дочернего элемента `Body`. Пространство имён не участвует в выборе.

## Пространство имён и WSDL

Пространство имён в файл не пишется. Для WSDL оно выводится как `urn:` плюс сегмент пути (`urn:testAccessGroup`). `GET /soap/testAccessGroup?wsdl` собирается из `table.json` и `soap.json`, в настройках его нет.

## Тело

Тело — те же имена, что у REST, только элементы вместо полей JSON. Повтор элемента — массив. Атрибуты не читаются.

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <findOne>
      <id>1</id>
    </findOne>
  </soap:Body>
</soap:Envelope>
```

| Операция | Дочерние элементы |
| --- | --- |
| `findAll` | `userFilters`, `userColumns`, `userOrder`, `userPagination` (`limit`, `offset`), `modifiers` |
| `findOne` | поля первичного ключа |
| `create` | колонки записи, `userReturnedColumns` |
| `updateOne`, `removeOne`, `softRemoveOne` | поля первичного ключа, колонки записи (для update), `userReturnedColumns` |
| `updateAll`, `removeAll`, `softRemoveAll` | `userFilters`, для update ещё колонки записи |

Составной ключ — несколько соседних элементов, по одному на колонку из `primaryKey`.

## Ответ

Успех: HTTP 200, `Body` содержит `<{операция}Response>` с тем же результатом, что REST отдаёт в JSON.

Ошибка приложения: HTTP 500 и `Fault`. `faultstring` — те же тексты, что у REST (`Запись не найдена`, `data не задан`). Нет конверта, нет операции в каталоге, тело больше лимита — HTTP 400 и `Fault` с `faultcode` `Client`.
