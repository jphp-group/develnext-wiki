# UXColor

- **class** `UXColor` (`php\gui\paint\UXColor`)
- **package** `gui`

```php
use php\gui\paint\UXColor;
```

Класс объектов, отвечающих за представление цвета в движке DevelNext. Обычно это цвет с поддержкой альфа-прозрачности - ARGB:
- `alpha, red, gree, blue` (`альфа, красный, зеленый, синий`).

> Объекты данного класса неизменяемые, чтобы создать новый цвет, нужно создать новый объект класса UXColor.

#### Свойства
> Все свойства только для чтения!

- `->`[`red`](#red-double) - _уровень красного_
- `->`[`green`](#green-double) - _уровень зеленого_
- `->`[`blue`](#blue-double) - _уровень синего_
- `->`[`opacity`](#opacity-double) - _прозрачность_
- `->`[`brightness`](#brightness-double) - _яркость_
- `->`[`hue`](#hue-double) - _оттенок_
- `->`[`saturation`](#saturation-double) - _насыщенность_
- `->`[`webValue`](#webvalue-string) - _HTML вид цвета_

#### Методы
- [Конструктор](#__construct) `__construct` - _создание цвета_
- `->`[`grayscale()`](#grayscale) - _черно-белый фильтр_
- `->`[`invert()`](#invert) - _инвертировать_
- `->`[`saturate()`](#saturate) - _более насыщенный цвет_
- `->`[`desaturate()`](#desaturate) - _менее насыщенный цвет_
- `->`[`interpolate()`](#interpolate) - _интерполяция цвета_
- `->`[`getRGB()`](#getrgb) - _RGB int значение цвета_
- `->`[`getWebValue()`](#getwebvalue) - _HTML вид цвета_

#### Статичные методы
- `UXColor:: `[`of()`](#of) - _создание цвета_
- `UXColor:: `[`rgb()`](#rgb) - _создание цвета из r, g, b_

---

## Свойства

### `red` (double)
Уровень красного от 0 до 1, где 1 = 100%.

---

### `green` (double)
Уровень зеленого от 0 до 1, где 1 = 100%.

---

### `blue` (double)
Уровень синего от 0 до 1, где 1 = 100%.

---

### `opacity` (double)
Уровень альфа-прозрачности цвета от 0 до 1, где 1 = 100% непрозрачности. 

---

### `brightness` (double)
Уровень яркости цвета от 0 до 1.

---

### `hue` (double)
Уровень оттенка (HUE) от 0 до 1.

---

### `saturation` (double)
Уровень насыщения цвета от 0 до 1.

---

### `webValue` (string)
Представление цвета в виде HTML цвета, строка начинающаяся с `#`, например `#637DFAC`.

---

## Методы

### `__construct()`
```php
__construct(double $r, double $g, double $b, double $opacity = 1.0)
```

```php
$r = 0.5;
$g = 0.6;
$b = 0.7;
$color = new UXColor($r, $g, $b, 0.8);
```

---

### `grayscale()`
```php
grayscale(): UXColor
```
Возвращает черно-белую версию цвета.

---

### `invert()`
```php
invert(): UXColor
```
Возвращает инвертированную версию цвета.

---

### `saturate()`
```php
saturate(): UXColor
```
Возвращает более насыщенную версию цвета.

---

### `desaturate()`
```php
desaturate(): UXColor
```
Возвращает менее насыщенную версию цвета.

---

### `interpolate()`
```php
interpolate(UXColor $color, double $t): UXColor
```
Возвращает интерполированную версию цвета.

---

### `getRGB()`
```php
getRGB(): int
```
Возвращает цвет в виде целого числа R, G, B.

---

### `getWebValue()`
```php
getWebValue(): string
```
Представление цвета в виде HTML цвета, строка начинающаяся с `#`, например `#637DFAC`.

---

## Статичные методы

### `of()`
```php
of(string $colorString): UXColor
```
Возвращает объект цвета исходя из переданной строки (это может быть HTML формат цвета).

```php
$color = UXColor::of('#FD73AC');
```

---

### `rgb()`
```php
rgb(int $r, int $g, int $b, double $opacity = 1.0): UXColor
```
Возвращает объект цвета исходя из R,G,B значений, где каждое значение это число от 0 до 255.

```php
$color = UXColor::rgb(120, 76, 230);
```