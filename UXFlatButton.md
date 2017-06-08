# UXFlatButton

- **class** <img src="https://cloud.githubusercontent.com/assets/1113915/22552153/c51aa54a-e968-11e6-9157-4153014038fd.png" align="top" /> `UXFlatButton` (`php\gui\UXFlatButton`) **extends** [`UXButtonBase`](UXButtonBase).
```php
use php\gui\UXFlatButton;
```

Класс компонента для отображения плоских кнопок.

> Изображение компонента:

> ![image](https://cloud.githubusercontent.com/assets/1113915/22552238/1ad0109c-e969-11e6-9083-1493cd4a3e01.png)

---

#### Свойства
- `->`[`color`](#color-uxcolor)
- `->`[`hoverColor`](#hovercolor-uxcolor)
- `->`[`clickColor`](#clickcolor-uxcolor)
- `->`[`borderRadius`](#borderradius-double)
- См. у класса родителя [`UXButtonBase`](UXButtonBase).

#### Методы
- [Конструктор (`new`)](#__construct) `__construct`
- См. у класса родителя [`UXButtonBase`](UXButtonBase).

---

## Свойства

### `color` ([UXColor](UXColor))
Основной цвет кнопки.

--

### `hoverColor` ([UXColor](UXColor))
Цвет кнопки при наведении курсора на неё.

--

### `clickColor` ([UXColor](UXColor))
Цвет кнопки при клике на неё.

--

### `borderRadius` (double)
Радиус закругления углов у кнопки, по-умолчанию `0`, что означает отсутствие закруглений.