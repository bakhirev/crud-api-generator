# Обьект context

Расширяемый обьект (Record<string, any>) типа JSON, который прокидывается между компонентами приложения.

## Структура данных

```
{
  table;
  executionSetting;
  queryParameters: Record<string, any>
  bodyParameters: Record<string, any>
  requestParameters: Record<string, any>
  requestHeaders?: Record<string, any>;
  traceId?: string | number;
  request?: any;
  response?: any;
}
```

`table` описание таблицы, см. `../configs/tables.md`
`executionSetting` параметры исполнения, см. `../configs/executionSettings.md`
`queryParameters` см. `getRequestParameters.md`
`bodyParameters` см. `getRequestParameters.md`
`requestParameters` см. `getRequestParameters.md`
`requestHeaders` заголовки запроса в формате `{ key: value }`
`traceId` индентификатор запроса
`request` обьект запроса, если данный язык / фреймворк предполагает его;
`response` обьект ответа, если данный язык / фреймворк предполагает его;

