# Класс `arr`

- **class** `arr` (`php\lib\arr`).
- **package** `std`.

```php
use php\lib\arr;
// или
use std;
```

Класс для работы с массивами и итераторами в php, состоит только из статических методов, экземпляр класса создать невозможно.

---

#### Статичные методы
- `arr ::`[`count()`](#count) - _количество элементов_
- `arr ::`[`has()`](#has) - _содержит ли элемент_
- `arr ::`[`toArray()`](#toarray) - _итератор в массив_
- `arr ::`[`of()`](#of) - _массив из итерируемого значения_
- `arr ::`[`toList()`](#tolist) - _превратить в список_
- `arr ::`[`keys()`](#keys) - _ключи массива_
- `arr ::`[`values()`](#values) - _значения массива_
- `arr ::`[`combine()`](#combine) - _массив из двух массивов ключей и значений_
- `arr ::`[`map()`](#map) - _map над массивом_
- `arr ::`[`flatten()`](#flatten) - _сделать массив плоским_
- `arr ::`[`sort()`](#sort) - _сортировка массива_
- `arr ::`[`sortByKeys()`](#sortbykeys) - _сортировка массива по ключам_
- `arr ::`[`peak()`](#peak) - _последний элемент_
- `arr ::`[`push()`](#push) - _добавить в конец_
- `arr ::`[`pop()`](#pop) - _удалить последний элемент и возвратить его_
- `arr ::`[`shift()`](#shift)
- `arr ::`[`unshift()`](#unshift) - _вставить элементы в начало_
- `arr ::`[`first()`](#first) - _первый элемент_
- `arr ::`[`firstKey()`](#firstkey) - _первый ключ массива_
- `arr ::`[`last()`](#last) - _последний элемент_
- `arr ::`[`lastKey()`](#lastkey) - _последний ключ_
- `arr ::`[`reverse()`](#reverse) - _перевернуть массив_

---

### `count()`
```php
arr::count(array|Countable|Iterator $collection): int
```
Метод возвращает количество элементов в массиве или в объекте-итераторе или в объекте, который реализует интерфейс Countable с методом `count()`.

> ⚠️ Внимание, для итераторов происходит полный перебор всех элементов для подсчета количества, поэтому, для больших списков операция может занять достаточно много времени!

```php
$array = [1, 2, 3, 4, 5];

$count = arr::count($array);


class Cars imlements Countable {
    function count() {
       return 3;
    }
}

$cars = new Cars();
$carCount = arr::count($cars); // carCount будет 3.
```

> ℹ️ Метод работает таким же образом как функция `count()` и `sizeof()` из классического php.

---

### `has()`
```php
arr::has(array|Traversable $collection, mixed $value, bool $strict = false): bool
```
Метод возвращает `true`, если в массиве или коллекции `$collection` есть значение `$value`. Можно задать строгость проверки через параметр `$strict`. Если проверка строгая, то кроме значений в массиве также будут сравниваться и типы как в операторе `===`.

```php
$array = ['banana', 'apple', 'plum'];

if (arr::has($array, 'banana')) {
    // в массиве есть banana.
}
```

> Метод немного напоминает по своей работе функцию `in_array()` из классического php.

---

### `toArray()`
```php
arr::toArray(array|Iterator $collection, bool $withKeys = false): array
```
Метод конвертирует итератор в массив, если передан массив вместо итератора, то возвратиться массив без ключей. По-умолчанию метод не сохраняет ключи итератора и массива `$collection`, но можно их сохранять, передав в параметр `$withKeys` значение `true`.

> ℹ️ В классическом php есть похожая функция `iterator_to_array()` или `array_values()`, если передать `$withKeys` как `false`.

---

### `of()`
Метод псевдоним к методу [`toArray()`](#toarray), см. выше.

---

### `toList()`
```php
arr::toList($collection, ...$others): array
```
Формирует список из массивов и обычных значений в единый одномерный массив. Чтобы понять, как работает функция, лучше взглянуть на пример:

```php
$list = arr::toList(['x' => 10, 20], 30, ['x' => 50, 60]);

var_dump($list);
// выведет [10, 20, 30, 50, 60]
```

---

### `keys()`
```php
arr::keys(array $array): array
```
Метод возвращает ключи массива `$array`, похожая функция `array_keys()`.

```php
$array = ['x' => 20, 'y' => 30];

var_dump(arr::keys($array)); // выведет ['x', 'y']
```

---

### `values()`
```php
arr::values(array|Iterator $array): array
```
> ⚠️ Метод появился начиная с DevelNext 16.5.0

Метод возвращает значения массива `$array`, похожая функция `array_values()`.

```php
$array = ['x' => 20, 'y' => 30];

var_dump(arr::values($array)); // выведет [0 => 20, 1 => 30]
```

---

### `combine()`
```php
arr::combine(array|Iterator $keys, array|Iterator $values): array
```
Формирует один массив из ключей `$keys` и значений `$values`. Метод похож на функцию `array_combine()`, однако умеет работать не только с массивами, но и с итераторами!

```php
$array = arr::combine(['x', 'y'], [20, 30]);

var_dump($array); // [x => 20, y => 30]
```

---

### `map()`
```php
arr::map(array|Iterator $collection, callable $callback): array
```
Метод формирует из массива или итератора `$collection` новый массив с помощью вызова коллбэка `$callback` для каждого элемента.

```php
$array = [1, 2, 3, 4, 5];

$newArray = arr::map($array, function ($value) { return $value + 1; });
// newArray --> [2, 3, 4, 5, 6];
```

> Вторым параметром в callback передается ключ перебираемого массива или итератора.

---

### `flatten()`
```php
arr::flatten(array|Iterator $collection, int $maxLevel = -1): array
```
Метод формирует одномерный массив из многомерного массива или итератора. `$maxLevel` - максимальный уровень вложенности, до которого пройдет метод, по-умолчанию `-1`, что означает - отсутствие максимума.

```php
// многомерный массив.
$array = [1, ['a', 'b'], [[333, 666], [77, 88]]];

$newArray = arr::flatten($array);
// newArray --> [1, 'a', 'b', 333, 666, 77, 88];
```

> См. также метод `arr ::`[`toList()`](#tolist).

---

### `sort()`
```php
arr::sort(array|Iterator $collection, callable $comparator = null, bool $saveKeys = false): array
```
Возвращает отсортированный массив, созданный на основе коллекции `$collection` (массив или итератор) с применением функции сравнения `$comparator`. По-умолчанию метод не сохраняет ключи, для этого есть параметр `$saveKeys`.

```php
$arr = [3, 9, 1, 4, 11];

$sortedArr = arr::sort($arr, function ($a, $b) {
   if ($a == $b) return 0;

   return $a < $b ? 1 : -1;
});

// sortedArr -> [1, 3, 4, 9, 11];
```

> Функция `$comparator` должна возвращать `0` если элементы равно, `1` - если элемент нужно помещать в начало, `-1` - если в конец.

---

### `sortByKeys()`
```php
arr::sortByKeys(array|Iterator $collection, callable $comparator = null, bool $saveKeys = false): array
```
Метод сортирует коллекцию `$collection` по её ключам, применяя для этого функцию `$comparator` для сравнения элементов. Функция очень похожа на `arr ::`[`sort()`](#sort), только сортирует по ключам, а не значениям. В функцию `$comparator` передаются ключи коллекции, а не значения как в `sort()`.

---

### `peak()`
```php
arr::peak(array $array): mixed
```
Возвращает последний элемент массива.

```php
$nums = [1, 2, 3, 5];

var_dump(arr::peak($nums)); // выведет 5!
```

---

### `push()`
```php
arr::push(array|ArrayAccess &$array, ...$values)
```
Добавляет элемент или несколько элементов в конец массива `$array` или объекта с реализацией `ArrayAccess`.

```php
$nums = [1, 2];

arr::push($nums, 3, 4, 5);

var_dump($nums); // выведет [1, 2, 3, 4, 5];
```

---

### `pop()`
```php
arr::pop(array &$array): mixed
```
Возвращает последний элемент массива и удаляет его. 

```php
$nums = [1, 2, 3, 4];

$lastNum = arr::pop($nums);

var_dump($lastNum); // выведет 4.
var_dump($nums); // выведет [1, 2, 3].
```

---

### `shift()`
```php
arr::shift(array &$array): mixed
```
Возвращает первый элемент массива и удаляет его.

```php
$nums = [1, 2, 3, 4];

$firstNum = arr::shift($nums);

var_dump($firstNum); // выведет 1.
var_dump($nums); // выведет [2, 3, 4].
```

---

### `unshift()`
```php
arr::unshift(array &$array, ...$values)
```
Добавляет в начало массива `$array` один или несколько элементов.

```php
$nums = [4, 5];

arr::unshift($nums, 1, 2, 3);

var_dump($nums); // выведет [1, 2, 3, 4, 5];
```

---

### `first()`
```php
arr::first(array|Traversable $collection): mixed
```
Возвращает первый элемент коллекции (массива или итератора).

---

### `firstKey()`
```php
arr::firstKey(array|Traversable $collection): string|int|null
```
Возвращает первый ключ коллекции (массива или итератора).

---


### `last()`
```php
arr::last(array $collection): mixed
```
> ⚠️ Метод появился начиная с DevelNext 16.5.0

Возвращает последний элемент массива.

```php
$arr = ['abc', 'xyz', 'foo', 'bar'];

$last = arr::last($arr);
alert($last); // покажет bar
```

---

### `lastKey()`
```php
arr::lastKey(array $collection): string|int|null
```
> ⚠️ Метод появился начиная с DevelNext 16.5.0

Возвращает последний ключ массива.

---

### `reverse()`
```php
arr::reverse(array $array): array
```
Возвращает перевернутый массив от `$array`.

```php
$array = [1, 2, 3];

$newArray = arr::reverse($array);

var_dump($newArray); // выведет [3, 2, 1].
```