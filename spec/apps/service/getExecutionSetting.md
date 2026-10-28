# getExecutionSetting

Функция, которая возвращает mixin JSON из `executionSetting`

## Входящие аргументы

`executionSetting` для конкретного метода;
`ID_модификатора[]` список модификаторов (опционально);

## Алгоритм работы

```
config = executionSetting.default || {};
for (ID_модификатора[]) {
  if (executionSetting[id]) {
    config = mixin(config, executionSetting[id]);
  }
}
return config;
```
