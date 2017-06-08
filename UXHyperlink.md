# UXHyperlink

- **class** <img src="https://cloud.githubusercontent.com/assets/1113915/23369179/8d17bd96-fd21-11e6-8115-54e6a64c63df.png" align="top" /> `UXHyperlink` (`php\gui\UXHyperlink`) **extends** [`UXButtonBase`](UXButtonBase).
```php
use php\gui\UXHyperlink;
```

Класс компонента для отображения ссылок, без форматирования.

> Изображение компонента:

> ![image](https://cloud.githubusercontent.com/assets/1113915/23369290/ea1f13f4-fd21-11e6-9b38-9aaf28adb256.png)

---

#### Свойства
- `->`[`visited`](#visited-bool).
- См. у класса родителя [`UXButtonBase`](UXButtonBase).

#### Методы
- [Конструктор (`new`)](#__construct) `__construct`
- См. у класса родителя [`UXButtonBase`](UXButtonBase).

---

### `visited` (bool)
Свойство возвращает `true`, если на ссылку уже кликали.

---

## Методы

### `__construct()`
```php
__construct(string $text = '', UXNode $graphic = null)
```

```php
$link = new UXHyperlink("Go to google.com");
$link->on('action', function () {
    browse('http://google.com');
}); 
```