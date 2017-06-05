# UXImage

- **class** `UXImage` (`php\gui\UXImage`)
- **package** `gui`

```php
use php\gui\UXImage;
```

Класс объектов, которые хранят изображения в памяти, в том числе и для GUI компонентов. Данный класс сам не является визуальным компонентом. 
> Если вам нужен класс визуального компонента "Изображения", смотрите [UXImageView](UXImageView) или [UXImageArea](UXImageArea).

#### Свойства
- `->`[`width`](#width-double) - _ширина_
- `->`[`height`](#height-double) - _высота_
- `->`[`progress`](#progress-double) - _прогресс загрузки_

#### Статичные методы
 - `UXImage ::`[`ofUrl()`](#ofurl) - _создать изображение из URL_

#### Методы
 - [Конструктор (`new`)](#__construct) `__construct` - _создание изображения_
 - `->`[`getPixelColor()`](#getpixelcolor) - _цвет пикселя_
 - `->`[`getPixelARGB()`](#getpixelargb) - _цвет пикселя в ARGB_
 - `->`[`cancel()`](#cancel) - _отмена загрузки_
 - `->`[`isError()`](#iserror) - _ошибка загрузки_
 - `->`[`isBackgroundLoading()`](#isbackgroundloading) - _фоновая ли загрузка_
 - `->`[`save()`](#save) - _сохранение изображения_

---

## Свойства

### `width` (double)
Ширина изображения в пикселях.

---

### `height` (double)
Высота изображения в пикселях.

---

### `progress` (double)
Прогресс загрузки изображения от 0 до 1, где 1 - это 100%.

---

## Методы

### `__construct()`
```php
__construct(Stream|string $stream [, bool $requiredWidth, bool $requiredHeight, $proportional = true])
```

```php
$image = new UXImage('path/to/image.png');
```

---

### `getPixelColor()`
```php
getPixelColor(int $x, int $y): UXColor
```
Возвращает цвет пикселя изображения по `x, y`, результат объект класса [UXColor](UXColor).

---

### `getPixelARGB()`
```php
getPixelARGB(int $x, int $y): int
```
Возвращает цвет пикселя изображения по `x, y` в виде целого числа, alpha прозрачность входит в это значение наряду с R, G и B.

---

### `cancel()`
Отменяет загрузку изображения, актуально для фоновых загрузок изображений по url.

---

### `isError()`
```php
isError(): bool
```
Возвращает `true` если при загрузке изображения произошла ошибка, например, формат изображения неверный. 

---

### `isBackgroundLoading()`
```php
isBackgroundLoading(): bool
```
Возвращает `true` если изображение еще загружается, актуально для фоновых загрузок изображений по url.

---

### `save()`
```php
save(Stream|string $to, string $format = 'png')
```
Сохраняет изображение в файл или поток (Stream) в формате `$format`. Поддерживаемые форматы:
- `png`
- `jpg`, `jpeg`
- `gif`

```php
$image->save('path/to/image.jpg', 'jpg');
```

---

## Статичные методы

### `ofUrl()`
```php
UXImage::ofUrl(string $url, bool $background = false): UXImage  
```
Загружает изображения по url.

```php
// фоновая загрузка изображения, $background - true
$image = UXImage::ofUrl('http://example.com/image.png', true); 
```