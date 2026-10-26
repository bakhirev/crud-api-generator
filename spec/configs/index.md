# Папка конфигурации

В ней находятся разного рода конфигурации системы

## Структура

```
./configs
  |
  |- http.json
  |- [Имя базы данных]
     |- [Имя таблицы из БД]
        |- table.json
        |- executionSettings.json
   
```
`table.json` описание одной таблицы, см. tables.md
`executionSettings.json` методов взаимодействия с таблицей, см. executionSettings.md
`http.json` одна схема запросов на все таблицы, см. http/index.md. Пишет парсер, см. `../apps/parser/dbServer.md`

