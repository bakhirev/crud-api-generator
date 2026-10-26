# Подключение к БД

Файл `configs/db.json`. Формат — аргумент конструктора [DBConnector](../components/db/Connector.md). Сканер читает его по умолчанию, см. [dbServer.md](../apps/parser/dbServer.md).

```
{
  host: string,
  port: string,
  database: string,
  user: string,
  password: string
}
```
