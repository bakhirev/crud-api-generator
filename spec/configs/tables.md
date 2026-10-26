# Описание таблиц в БД

В виде JSON следующего вида

## Таблица

```
{
  table: string,
  primaryKey: string[],
  columns: Record<ID_колонки, Описание колонки>,
}
```
`table` название таблицы [A-Za-z_0-9]+
`primaryKey` список колонок, которые являются первичным ключом.
`columns` описание колонок, ID_колонки формата [A-Za-z_0-9]+

## Описание колонки

```
{
  type: string,
  required?: boolean,
  min?: number,
  max?: number,
  value?: any,
  description?: string,
}
```
`type` тип данных в колонке. Из спеки DB или текущего языка программирования. Базовые "number", "string", "boolean"
`required` обязательность заполнения
`value` значение по умолчанию
`min`, `max` минимальное и максимальное значение для числового типа, или минимальная и максимальная длина для типа string
`description` описание колонки

