# UXLabel

- **class** <img src="https://cloud.githubusercontent.com/assets/1113915/22618547/46438f0a-eaf0-11e6-8e88-689f576cb5b6.png" align="top" /> `UXLabel` (`php\gui\UXLabel`) **extends** [`UXLabeled`](UXLabeled).
```php
use php\gui\UXLabel;
```

Класс компонента для отображения обычных текстов, без форматирования, с возможностью выбрать шрифт и иконку для текста. У класса есть потомок `UXLabelEx`, который добавляет функцию авторазмера.

> Изображение компонента:

> ![image](https://cloud.githubusercontent.com/assets/1113915/22618557/ac634d7a-eaf0-11e6-815d-ceaf89a07515.png)

---

#### Свойства
- `->`[`labelFor`](#labelfor-uxnode)
- `->`[`autosize`](#autosize-bool) (только у потомка `UXLabelEx`).
- См. у класса родителя [`UXLabeled`](UXLabeled).

#### Методы
- [Конструктор (`new`)](#__construct) `__construct`
- См. у класса родителя [`UXLabeled`](UXLabeled).

---

## Свойства

### `labelFor` ([UXNode](UXNode))
Привязка текста к определенному визуальному компоненту интерфейса. По-умолчанию `null`.

---

### `autosize` (bool)
> Только у класса `UXLabelEx`.

Авторазмер текста, если включен, то ширина и высота компонента будут рассчитываться в зависимости от [текста](UXLabeled#text-string) компонента.

---

## Методы

### `_construct`
```php
__construct([$text = '', UXNode $graphic = null]) {}
```
Конструктор класса UXLabel.
```php
$icon = new UXImageView(new UXImage('path/to/image.png'));
$label = new UXLabel('Текст компонента', $icon);
```