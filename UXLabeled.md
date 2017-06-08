# UXLabeled

- abstract **class** `UXLabeled` (`php\gui\UXLabeled`) **extends** [`UXControl`](UXControl).

> Классы наследники:

> [`UXButtonBase`](UXButtonBase), [`UXLabel`](UXLabel).

Базовый абстрактный класс всех текстовых объектов, таких как кнопки, тексты и т.п.

---

#### Свойства
- `->`[`alignment`](#alignment-string) - _выравнивание_
- `->`[`textAlignment`](#textalignment-string) - _выравнивание текста_
- `->`[`wrapText`](#wraptext-bool) - _авто-перенос текста_
- `->`[`underline`](#underline-bool) - _подчеркивать текст_
- `->`[`text`](#text-string) - _текст_
- `->`[`textColor`](#textcolor-uxcolor) - _цвет текста_
- `->`[`font`](#font-uxfont) - _шрифт текста_
- `->`[`graphic`](#graphic-uxnode) - _иконка_
- `->`[`graphicTextGap`](#graphictextgap-double) - _отступ текста от иконки_
- `->`[`ellipsisString`](#ellipsisstring-string) - _текст сокращения_
- `->`[`contentDisplay`](#contentdisplay-string) - _место отображения иконки_
- `->`[`mnemonicParsing`](#mnemonicparsing-bool) - _обрабатывать спец. символы в тексте_
- См. у класса родителя [`UXControl`](UXControl).

#### Методы
- См. у класса родителя [`UXControl`](UXControl).

---

## Свойства

### `alignment` (string)
Выравнивание текста внутри области всего компонента, учитывается ширина и высота компонента, по-умолчанию `BASELINE_CENTER`.
```php
'BASELINE_LEFT' // слева и по центру текста написания.
'BASELINE_CENTER' // по-центру относительно текста написания.
'BASELINE_RIGHT' // справа и по центру текста написания.
'TOP_LEFT' // сверху-слева.
'TOP_CENTER' // сверху, в центре.
'TOP_RIGHT' // сверху-справа.
'BOTTOM_LEFT' // снизу-слева.
'BOTTOM_CENTER' // снизу, в центре.
'BOTTOM_RIGHT' // снизу-справа.
```

---

### `textAlignment` (string)
Выравнивание текста относительно его написания, а не ширины контейнера, по-умолчанию `LEFT`.

```php
'LEFT' // к левой стороне
'CENTER' // к центру
'RIGHT' // к правой стороне
'JUSTIFY' // растягивать к обоим сторонам
```

---

### `wrapText` (bool)
Переводить текст на новую строку, если не хватает ширины контейнера текста. По-умолчанию `false`.

---

### `underline` (bool)
Подчеркивать текст, по-умолчанию `false`.

---

### `text` (string)
Текст компонента, по-умолчанию - пустая строка.

---

### `textColor` ([UXColor](UXColor))
Цвет текста компонента.

---

### `font` ([UXFont](UXFont))
Шрифт текста компонента. По-умолчанию системный шрифт [`UXFont::getDefault()`](UXFont#getdefault).

---

### `graphic` ([UXNode](UXNode))
Иконка компонента, любой визуальный компонент, в том числе и изображения.

```php
// задать иконку
$image = new UXImage('path/to/image.png');
$this->button->graphic = new UXImageView($image);
```

---

### `graphicTextGap` (double)
Разрыв между иконкой и текстом в пикселях, по-умолчанию `4`.

---

### `ellipsisString` (string)
Текст сокращения, отображается тогда, когда не хватает ширины контейнера под текст компонента и только если отключено свойство [`wrapText`](#wraptext-bool). По-умолчанию три точки `'...'`.

---

### `contentDisplay` (string)
Где и как размещать текст и иконку внутри компонента, по-умолчанию `'LEFT'`, что означает - размещать иконку слева от текста. Возможные значения:
```php
'LEFT' // иконка слева
'TOP' // иконка сверху
'RIGHT' // иконка справа
'BOTTOM' // иконка внизу
'TEXT_ONLY' // только текст, без иконки
'GRAPHIC_ONLY' // только иконка, без текста
```

---

### `mnemonicParsing` (bool)
Обрабатывать ли текстовые специальные сочетания символов, по-умолчанию `false` для [UXMenuItem](UXMenuItem), для остальных `true`.