# Класс DBConnector

Выполняет подключение к базе данных.
Держит открытый пул коннектов.

## Конструктор

Конструктор принимает JSON конфиг для подключения к базе данных ввиде:

```
{
  host: string;
  port: string;
  database: string;
  user: string;
  password: string;
}
```

## Методы

`connect` - подключиться
`reconnect` - переподключиться
`query` - выполнить запрос (первый аргумент запрос, второй параметры запроса)

### Выходной формат метода Query 

```
{
  status: boolean,
  response: any,
  errorMessage: string
}
```

`status` - `true` если запрос прошел без ошибок
`response` - результат в формате JSON или null
`errorMessage` - сообщение об ошибке, если запрос упал. Иначе пустая строка