# UXToggleButton

- **class** <img src="https://cloud.githubusercontent.com/assets/1113915/22553003/30707f10-e96c-11e6-8912-5b2195295490.png" align="top" /> `UXToggleButton` (`php\gui\UXToggleButton`) **extends** [`UXButtonBase`](UXButtonBase).
```php
use php\gui\UXToggleButton;
```

Класс компонента для отображения кнопок-переключателей.

> Изображение компонента:

> ![image](https://cloud.githubusercontent.com/assets/1113915/22553066/6f652a18-e96c-11e6-8510-9f0ab76c8499.png)

---

#### Свойства
- `->`[`selected`](#selected-bool)
- `->`[`toggleGroup`](#togglegroup-uxtogglegroup)
- См. у класса родителя [`UXButtonBase`](UXButtonBase).

#### Методы
- [Конструктор (`new`)](#__construct) `__construct`
- См. у класса родителя [`UXButtonBase`](UXButtonBase).

---

## Свойства

### `selected` (bool)
Выделена ли кнопка или нет, по-умолчанию `false`.

---

### `toggleGroup` (UXToggleGroup)
Группа переключателей, к которой кнопка принадлежит. Можно добавить несколько кнопок в одну группу, чтобы среди них можно было включить только одну.

```php
$group = new UXToggleGroup();

$button1 = new UXToggleButton();
$button1->toggleGroup = $group;

$button2 = new UXToggleButton();
$button2->toggleGroup = $group;
```