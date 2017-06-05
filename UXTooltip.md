# UXTooltip

- **class** `UXTooltip` (`php\gui\UXTooltip`)
- наследует класс [`UXPopupWindow`](UXPopupWindow) (`php\gui\UXPopupWindow`)
 - все его методы и свойства

```php
use php\gui\UXTooltip;
```

Класс для создания всплывающих подсказок с текстом и графикой.

---

#### Свойства
- `->`[`text`](#text-string) - _Текст_
- `->`[`textAlignment`](#textalignment-string) - _Выравнивание текста_
- `->`[`textOverrun`](#textoverrun-string) - _Сокращение текста_
- `->`[`font`](#font-uxfont) - _Шрифт_
- `->`[`graphic`](#graphic-uxnode) - _Графика_
- `->`[`graphicTextGap`](#graphictextgap-double) - _Отступ для графики_
- `->`[`activated`](#activated-bool) - _Активность_
- `->`[`wrapText`](#wraptext-bool) - _Переносить текст_

#### Статичные методы
- `UXTooltip ::`[`of()`](#of) - _создать подсказку_
- `UXTooltip ::`[`install()`](#install) - _установить подсказку_
- `UXTooltip ::`[`uninstall()`](#uninstall) - _удалить подсказку_

---

## Свойства

### `text` (string)
Текст подсказки.

---

### `textAlignment` (string)
Выравнивание текста, возможные значения:
```php
'LEFT' // к левой стороне
'RIGHT' // к правой стороне
'CENTER' // к центру
'JUSTIFY' // к обоим сторонам
```

---

### `textOverrun` (string)
Как сокращать текст, если не хватает области для его отображения, возможные значения:
```php
'CLIP', 'ELLIPSIS', 'WORD_ELLIPSIS', 'CENTER_ELLIPSIS', 'CENTER_WORD_ELLIPSIS', 
'LEADING_ELLIPSIS', 'LEADING_WORD_ELLIPSIS'
```

---

### `font` ([UXFont](UXFont))
Шрифт текста подсказки.

---

### `graphic` ([UXNode](UXNode))
Иконка подсказки, может быть любым визуальным компонентом, в том числе и [`UXImageView`](UXImageView).

---

### `graphicTextGap` (double)
Отступ между текстом и подсказкой в пикселях. 

---

### `activated` (bool)
Активирована ли подсказка или нет.

---

### `wrapText` (bool)
Переносить текст на новую строку, если не хватает ширины области отображения подсказки.

---

## Статичные методы

### `of()`
```php
of($text[, UXNode $graphic])
```
Метод-конструктор подсказки с текстом и иконкой, иконка необязательный аргумент.

```php
$icon = new UXImageView(new UXImage('path/to/file.png'));
$tooltip = UXTooltip::of('Моя подсказка', $icon);
```

---

### `install()`
```php
install(UXNode $node, UXTooltip $tooltip)
```
Установить компоненту `$node` подсказку, которая будет отображаться при наведении курсора.

```php
$tooltip = new UXTooltip();
$tooltip->text = 'Это кнопка';

UXTooltip::install($this->button, $tooltip);
```

> Вместо данного метода можно использовать свойство `tooltip` у визуального компонента:
```php
$tooltip = new UXTooltip();
$tooltip->text = 'Это кнопка';
$button->tooltip = $tooltip;
```

---

### `uninstall()`
```php
uninstall(UXNode $node, UXTooltip $tooltip)
```
Убирает переданную подсказку с компонента `$node`.