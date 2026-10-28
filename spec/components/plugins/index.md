# Плагинизатор (синглтон)

Обеспечивает модификацию данных на разных этапах и добавляет функционал.
Содержит в себе список плагинов из папки `./plugins`.

```
plugins = [
  new Plugin1(),
  new Plugin2(),
];

function apply(...args) {
  for (plugin in plugins) plugin.apply(...args);
}
```

## Плагин

```
class Plugin {
  constructor() {
    this.id = string; // индентификатор плагина
  }
  apply(code: string,  context) {
    // код плагина
  }
}
```

Аргументы apply:

`code` - `string`, индентификатор места вызова плагина.
`context` - `string`, индентификатор места вызова плагина.
`
