# getRequestParameters

Извлекает и конвертирует параметры запроса. Возвращает обьект.

## Структуры данных

### Input arguments

`type` - string, протокол передачи данных (soap, xml, json, multipart/form-data, OData, protobuf). Правила обработки каждого протокола хранятся в отдельном файле.
`request` - обьект запроса (если нужен для данной среды исполнения). Например, PHP берет данные из глобальных $_GET, $_POST и для него этот аргумент может отсутствовать.

### Return value
```
{
  queryParameters: Record<string, any>
  bodyParameters: Record<string, any>
  requestParameters: Record<string, any>
}
```

`queryParameters` - параметры из URL запроса
`bodyParameters` - параметры из тела запроса
`requestParameters` - мерж `queryParameters` + `bodyParameters` отфильтрованных по `allowedParameters`