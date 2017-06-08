# Geometry

- **class** `Geometry` (`action\Geometry`)
```php
use action\Geometry;
```

Утилитный класс только со статичными методами, для работы с простыми геометрическими фигурами.

> У класса приватный конструктор, невозможно создать объект данного класса.

---

#### Статичные методы

- `Geometry ::`[`hasPoint()`](#haspoint)
- `Geometry ::`[`intersect()`](#intersect)

---

### `hasPoint()`
```php
hasPoint(object $what, double $x, double $y): bool
```
Метод возвращает `true`, если точка `$x, $y` входит внутрь фигуры объекта `$what`. Объектом может выступать абсолютно любой объект php, у которого есть свойства `x, y, width и height`.

```php
if (Geometry::hasPoint($button, 100, 300)) {
   alert("Точка (x: 100, y: 300) находится внутри кнопки");
}
```

---

### `intersect()`
```php
intersect(object $one, object $two): bool
```
Возвращает `true`, если два прямоугольника объекта `$one` и `$two` пересекаются. В качестве объекта могут быть любые объекты php, у которых есть свойства `x, y, width и height`.

```php
if (Geometry::intersect($button1, $button2)) {
   // кнопки button1 и button2 пересекаются.
}
```