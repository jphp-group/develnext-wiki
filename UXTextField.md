# UXTextField

- **class** <img src="https://cloud.githubusercontent.com/assets/1113915/23470109/9b7f01a0-feb6-11e6-8e6b-4b6915bc5214.png" align="top" /> `UXTextField` (`php\gui\UXTextField`) **extends** [`UXTextInputControl`](UXTextInputControl).
```php
use php\gui\UXTextField;
```

Класс компонента для поле ввода текста в одну строку.

> Изображение компонента:

> ![image](https://cloud.githubusercontent.com/assets/1113915/23470269/0260734a-feb7-11e6-9d09-65ee103220e9.png)

---

#### Свойства
- `->`[`alignment`](#alignment-string)
- `->`[`prefColumnCount`](#prefcolumncount-int)
- См. у класса родителя [`UXTextInputControl`](UXTextInputControl).

#### Методы
- [Конструктор (`new`)](#__construct) `__construct`
- См. у класса родителя [`UXTextInputControl`](UXTextInputControl).

---

## Свойства

### `alignment` (string)
Выравнивание текста внутри компонента, по-умолчанию `'LEFT'` - выравнивание к левой стороне. Возможные варианты:
```php
'LEFT' // левое выравнивание
'CENTER' // центральное выравнивание
'RIGHT' // правое выравнивание
```

---

### `prefColumnCount` (int)
Количество колонок у поля ввода, по-умолчанию `1`.

---

## Методы

### `__construct()`
```php
__construct(string $text = '')
```

```php
$field = new UXTextField("Text");
```