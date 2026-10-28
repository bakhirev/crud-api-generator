# HTTP

Обёртка над `service`, которая позволяет обращаться к нему через http соединение.

Поднимает web-сервер и слушает определенный порт (для nodejs, java). Является входной точкой (для php).
Обрабатывает входящие запросы. Прокидывает их в соответствующий метод `service`. Отправляет ответ клиенту.

## Пример URL адресов

`/{type}/{descriptiop}`

`type` тип протокола (`rest`, `soap`, `odata`, `graphql`). Если нет, не распознан или не соответствует списку, то `rest`.
`descriptiop` URL часть внутри протокола. См. описание в отдельных файлах. Для `rest` см. `./rest.md`.

## Выбор схемы ответа
Если протокол предполагает определенную схему ответа, выбираем её.

Иначе смотрим заголовок `Accept`, чтобы знать тип ответа
  Если есть `application/xml` XML
  Иначе `JSON`

## Структура кода`
http
  [component] (request|file|webSocket|MCP|...)
    getURLScheme
      [component] (rest|django|OData|...)

    plugins.apply("http-before-get-params", context);
    getRequestParameters
      [component] (soap|xml|OData|rest|...)
    plugins.apply("http-after-get-params", context);

    service();

    plugins.apply("http-before-send-response", context);
    sendResponse
      [component] (soap|xml|OData|rest|...)
