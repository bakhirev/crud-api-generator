# Описание запросов для HTTP-сервиса

## Описание схемы запросов

```
{
  [url]: {
    [requestMethod]: Настройки запроса
  },
}
```
`url` URL адрес. Переменные выделяются фигурными скобками. Например `/users/{id}?status={status}`
`requestMethod` метод (`GET`, `POST`, `PUT`, `DELETE`, etc)

## Настройки запроса

```
{
  method: string
}
```

`method` компонент у service, который нужно вызвать.

## Пример для REST схемы:

```
{
  "/users": {
    "get": { "method": "findAll" },
    "post": { "method": "create" },
  },
  "/users/{id}": {
    "get": { "method": "findOne" },
    "update": { "method": "updateOne" },
    "patch": { "method": "updateOne" },
  }
}
```

