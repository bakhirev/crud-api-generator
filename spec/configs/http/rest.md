# Правила описания REST адресов

`/{table}/{primaryKey}`

`table` название таблицы из `tables.md` в lowerCamelCase.
`primaryKey` переменная primaryKey для этой таблицы (id, uuid и т.п.) или фиксированное название общего метода (например: `updateAll`)

Примеры:

`/users/updateAll`
`/users/removeAll`
`/users/softRemoveAll`
`/users/123`


