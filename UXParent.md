# UXParent

- **class** `UXParent` (`php\gui\UXParent`) **extends** [`UXNode`](UXNode).

> Классы наследники:

> [`UXRegion`](UXRegion), [`UXWebView`](UXWebView)

---

#### Свойства
- `->`[`childrenUnmodifiable`](#childrenunmodifiable-uxlist) - _внутренние компоненты_
- `->`[`stylesheets`](#stylesheets-uxlist) - _список css стилей в виде ресурсов_
- См. у класса родителя [`UXNode`](UXNode).

#### Методы
- `->`[`findFocusedNode()`](#findfocusednode) - _найти внутри объект с фокусом_
- `->`[`requestLayout()`](#requestLayout) - _перевести фокус на объект_
- См. у класса родителя [`UXNode`](UXNode).

---

## Свойства

### `childrenUnmodifiable` ([UXList](UXList))
Список компонентов "детей", которые находятся внутри компонента.

---

### `stylesheets` ([UXList](UXList))
Список файлов со стилями css, которые применяются к компоненту.

---

## Методы
 
### `findFocusedNode()`
```php
findFocusedNode(): UXNode | null
```
Возвращает внутренний компонент, на котором находится фокус.

---

### `requestLayout()`
Пересчитывает размеры и позицию компонента, относительно его родителя-слоя.
