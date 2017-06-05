# UXScreen
- **class** `UXScreen` (`php\gui\UXScreen`)
- **package** `gui`

```php
use php\gui\UXScreen;
```

Класс для работы с разрешением экрана пользователя. У класса приватный конструктор, объекты UXScreen можно получить только через статичные методы:

---

#### Свойства
> Все свойства только для чтения!

- `->`[`dpi`](#dpi-double) - _DPI экрана_
- `->`[`bounds`](#bounds-array) - _размеры экрана_
- `->`[`visualBounds`](#visualbounds-array) - _размеры рабочей области экрана_

#### Статичные методы
- `UXScreen ::`[`getPrimary()`](#getprimary) - _главный экран_
- `UXScreen ::`[`getScreens()`](#getscreens) - _список всех экранов_

---

## Свойства

### `dpi` (double)
DPI значение экрана. [https://ru.wikipedia.org/wiki/Dots_per_inch](https://ru.wikipedia.org/wiki/Dots_per_inch)

---

### `bounds` (array)
Размеры экрана в виде массива:
```php
['x' => 0, 'y' => 0, 'width' => 0, 'height' => 0]
```

---

### `visualBounds` (array)
Визуальные параметры экрана в виде массива:
```php
['x' => 0, 'y' => 0, 'width' => 0, 'height' => 0]
```

> Данный метод учитывает только рабочую область экрана, не захватывая таскбар операционной системы.

---

## Статичные методы

### `getPrimary()`
Возвращает основной экран пользователя в виде объекта класса `UXScreen`.

```php
$screen = UXScreen::getPrimary();

$x = $screen->bounds['x'];
$y = $screen->bounds['y'];
$width = $screen->bounds['width'];
$height = $screen->bounds['height'];
```

---

### `getScreens()`
Возвращает список экранов в виде массива объектов класса `UXScreen`:

```php
$screens = UXScreen::getScreens();

foreach ($screens as $screen) {
   pre($screen);
}
```