# Класс `reflect`

- **class** `reflect` (`php\lib\reflect`).
- **package** `std`

```php
use php\lib\reflect;
// или
use std;
```
Утилитный класс для работы с рефлексией в php, позволяет получать необходимую информацию о классах и типах.

---

#### Статичные методы

- `reflect ::`[`typeOf()`](#typeof)
- `reflect ::`[`typeModule()`](#typemodule)
- `reflect ::`[`functionModule()`](#functionmodule)
- `reflect ::`[`newInstance()`](#newinstance)

---

### `typeOf()`
```php
typeOf(object $object, bool $toLowerCase = false): string
```
Метод возвращает название класс объекта `$object`, параметр `$toLowerCase` позволяет приводить название класса всегда в нижний регистр, если это необходимо.

```php
class Car { }

$car = new Car();

var_dump( reflect::typeOf($car) ); // выведет Car.
```

---

### `typeModule()`
```php
typeModule(string $typeName): php\lang\Module
```
Метод возвращает модуль класса в виде объекта [Module](Module).

---

### `functionModule()`
```php
functionModule(string $funcName): php\lang\Module
```
Метод возвращает модуль функции в виде объекта [Module](Module).

---

### `newInstance()`
```php
newInstance(string $className, array array $args = null, bool $withConstruct = true): object
```
Создает объект класса `$className` с передачей аргументов конструктору класса из массива `$args`. Можно отключить вызов конструктора при создании объекта через аргумент `$withCounstruct`.