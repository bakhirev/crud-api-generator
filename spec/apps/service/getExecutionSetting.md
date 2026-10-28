# getExecutionSetting

Функция, которая возвращает mixin JSON из `executionSetting`

## Входящие аргументы

`executionSetting` для конкретного метода;
`methodName[]` список модификаторов (опционально);

## Алгоритм работы

```
config = executionSetting.default || {};
for (methodName[]) {
  if (executionSetting[id]) {
    config = mixin(config, executionSetting[id]);
  }
}
return config;
```
