# Класс `str`

- **class** `str` (`php\lib\str`).
- **package** `std`.

```php
use php\lib\str;
// или
use std;
```

Класс для работы со строками в php, состоит только из статических методов, экземпляр класса создать невозможно.

---

#### Статичные методы

- **Поиск по строке**
  - `str :: `[`pos()`](#pos) - _позиция подстроки_
  - `str :: `[`posIgnoreCase()`](#posignorecase) - _позиция подстроки без регистро-зависимости_
  - `str :: `[`lastPos()`](#lastpos) - _позиция подстроки с конца_
  - `str :: `[`lastPosIgnoreCase()`](#lastposignorecase) - _позиция строки с конца без регистро-зависимости_
  - `str :: `[`contains()`](#contains) - _содержит ли строку_
  - `str :: `[`count()`](#count) - _количество подстрок в строке_

- **Сравнение строк**
  - `str :: `[`compare()`](#compare) - _сравнение 2х строк_
  - `str :: `[`compareIgnoreCase()`](#compareignorecase) - _сравнение 2х строк без регистро-зависимости_
  - `str :: `[`equalsIgnoreCase()`](#equalsignorecase) - _равны ли 2 строки не учитывая регистр_
  - `str :: `[`startsWith()`](#startswith) - _начинается ли строка с подстроки_
  - `str :: `[`endsWith()`](#endswith) - _кончается ли строка подстрокой_
  - `str :: `[`isNumber()`](#isnumber) - _является ли строка числом_
  - `str :: `[`isLower()`](#islower) - _все ли символы в строке в нижнем регистре_
  - `str :: `[`isUpper()`](#isupper) - _все ли символы в строке в верхнем регистре_

- **Преобразование строк**
  - `str :: `[`sub()`](#sub) - _подстрока от строки_
  - `str :: `[`lower()`](#lower) - _строка в нижнем регистре_
  - `str :: `[`lowerFirst()`](#lowerfirst) - _строка с первым символом в нижнем регистре_
  - `str :: `[`upper()`](#upper) - _строка в верхнем регистре_
  - `str :: `[`upperFirst()`](#upperfirst) - _строка с первым символом в нижнем регистре_
  - `str :: `[`length()`](#length) - _длина строки_
  - `str :: `[`replace()`](#replace) - _заменить в строке_
  - `str :: `[`repeat()`](#repeat) - _повторить строку несколько раз_
  - `str :: `[`trim()`](#trim) - _убрать пустые символы строки слева и справа_
  - `str :: `[`trimRight()`](#trimright) - _убрать пустые символы строки только справа_
  - `str :: `[`trimLeft()`](#trimleft) - _убрать пустые символы строки только слева_
  - `str :: `[`reverse()`](#reverse) - _перевернуть строку_
  - `str :: `[`shuffle()`](#shuffle) - _перемешать символы в строке в случайном порядке_
  - `str :: `[`random()`](#random) - _сгенерировать случайную строку_
  - `str :: `[`split()`](#split) - _строка в массив с разделителем_
  - `str :: `[`join()`](#join) - _массив в строку с разделителем_
  - `str :: `[`encode()`](#encode) - _кодирование строки_
  - `str :: `[`decode()`](#decode) - _декодирование строку в родную кодировку_
  - `str :: `[`format()`](#format) - _форматирование строки_
  - `str :: `[`uuid()`](#uuid) - _uuid генератор строк_
  - `str :: `[`hash()`](#hash) - _хеширование строки_
  - `str :: `[`lines()`](#lines) - _многострочный текст в массив_

---

### `pos()`
```php
str::pos(string $string, string $search, int $fromIndex = 0): int
```
Метод ищет подстроку `$search` в строке `$string` и возвращает её позицию (начиная с нуля). Если ничего не было найдено, метод вернет `-1`. Метод учитывает регистр символов и позволяет начинать поиск с определенного по счету символа `$fromIndex`.

```php
$search = 'родилась';
$string = 'В лесу родилась ёлочка';

$pos = str::pos($string, $search);

alert('Позиция = ' . $pos);
```

---

### `posIgnoreCase()`
```php
str::posIgnoreCase(string $string, string $search, int $fromIndex = 0): int
```
> Метод не учитывает регистр символов при поиске. См. также [`pos()`](#pos).

Метод ищет подстроку `$search` в строке `$string` и возвращает её позицию (начиная с нуля). Если ничего не было найдено, метод вернет `-1`. Метод позволяет начинать поиск с определенного по счету символа `$fromIndex`. 

---

### `lastPos()`
```php
str::lastPos(string $string, string $search, int $fromIndex = null): int
```
> Метод учитывает регистр символов при поиске.

Метод ищет подстроку `$search` в строке `$string` начиная с конца строки и возвращает её позицию (начиная с нуля). Если ничего не было найдено, метод вернет `-1`. Метод позволяет начинать поиск с определенного по счету символа `$fromIndex`, по-умолчанию он равен `null`, что означает - искать, начиная с последнего символа строки. 

```php
$string = 'ту-ту-ру';
$search = 'ту';

$pos = str::lastPos($string, $search);
// $pos будет равен 3, а не 0, т.к. поиск идет с конца.
```

---

### `lastPosIgnoreCase()`
```php
str::lastPosIgnoreCase(string $string, string $search, int $fromIndex = null): int
```
> Метод не учитывает регистр символов при поиске. См. также [`lastPos()`](#lastPos).

Метод ищет подстроку `$search` в строке `$string` начиная с конца строки и возвращает её позицию (начиная с нуля). Если ничего не было найдено, метод вернет `-1`. Метод позволяет начинать поиск с определенного по счету символа `$fromIndex`, по-умолчанию он равен `null`, что означает - искать, начиная с последнего символа строки. 

---

### `sub()`
```php
str::sub(string $string, int $beginIndex, int $endIndex = null): string
```
Метод возвращает подстроки из строки `$string` начиная с `$beginIndex` по счету символа (включительно) и до `$endIndex` символа (не включительно). Параметр `$endIndex` не обязательный, если его не передать, то подстрока будет скопирована до конца строки `$string`. Индексация символов начинается с нуля.

```php
$string = 'Hello World';

alert(str::sub($string, 6)); // выведет World, W - 6 символ.
alert(str::sub($string, 6, 9)); // выведет Wor, l - 9 символ.
```

---

### `compare()`
```php
str::compare(string $string1, string $string2): int
```
Сравнивает две строки и возвращает результат в виде числа, где:
- `0` - означает, что строки равны.
- `больше 0` - строка `$string1` больше `$string2`.
- `меньше 0` - строка `$string1` меньше `$string2`.

---

### `compareIgnoreCase()`
```php
str::compareIgnoreCase(string $string1, string $string2): int
```
Сравнивает две строки и возвращает результат в виде числа. Метод идентичен [`compare()`](#compare), за исключением того, что он при сравнении игнорирует регистр символов сравниваемых строк.

---

### `equalsIgnoreCase()`
```php
str::equalsIgnoreCase(string $string1, string $string2): bool
```
Возвращает `true` если две строки равны друг другу без учета регистра символов.
```php
if (str::equalsIgnoreCase('ПРИВЕТ', 'привет')) {
   alert('ПРИВЕТ == привет, без учета регистра символов');
}
```
> См. также [`compareIgnoreCase()`](#compareignorecase).

---

### `startsWith()`
```php
str::startsWith(string $string, string $prefix, int $offset = 0): bool
```
Возвращает `true` если строка `$string` начинается с префикс-строки `$prefix`. Можно указать, с какого символа по счету проверять префикс через третий аргумент `$offset` (индексация идет с нуля).

```php
$string = 'gamedev';

if (str::startsWith($string, 'game')) {
    alert('Строка начинается со слова game');
}
```
> См. также [`endsWith()`](#endswith).

---

### `endsWith()`
```php
str::endsWith(string $string, string $suffix): bool
```
Возвращает `true` если строка `$string` оканчивается суффикс-строкой `$suffix`. 

```php
$string = 'file.mp3';

if (str::endsWith($string, '.mp3')) {
    alert('Строка оканчивается на ".mp3"');
}
```

> См. также [`startsWith()`](#startswith).

---

### `isNumber()`
```php
str::isNumber(string $string, string $bigNumbers = true): bool
```
Возвращает `true` если строка `$string` является целым числом. `$bigNumbers` по-умолчанию `true`, что означает, что функция будет возвращать `true` даже для бесконечно больших строковых чисел, с которым невозможно простым путем совершать математические операции в php.

```php
var_dump(str::isNumber('3784798738304908048498498')); // выведет true.
var_dump(str::isNumber('39874dhfj')); // выведет false.
var_dump(str::isNumber('00304')); // выведет true.
var_dump(str::isNumber('3389e4')); // выведет false.
var_dump(str::isNumber('3.49')); // выведет false.
var_dump(str::isNumber('23  ')); // выведет false.
```

---

### `isLower()`
```php
str::isLower(string $string): bool
```
Возвращает `true` если все символы в строке `$string` в нижнем регистре.

---

### `isUpper()`
```php
str::isUpper(string $string): bool
```
Возвращает `true` если все символы в строке `$string` в верхнем регистре.

---

### `contains()`
```php
str::contains(string $string, string $search): bool
```
Осуществляет поиск подстроки `$search` в строке `$string` и если подстрока найдена, возвращает `true`.

```php
$nickname = 'devel.next';

if (str::contains($nickname, '.')) {
    alert('Ник содержит точку');
}
```

---

### `count()`
```php
str::count(string $string, string $subString, int $offset = 0): int
```
Возвращает число вхождений подстроки `$subString` в строку `$string` начиная с символа `$offset` (по-умолчанию с начала строки).

```php
$string = 'hello develnext';

$eCount = str::count($string, 'e');
alert("В строке $eCount шт. символов 'e'");
```

---

### `lower()`
```php
str::lower(string $string): string
```
Конвертирует все символы строки '$string' в нижний регистр, возвращает полученную строку.

```php
$string = 'Привет Мир';

alert(str::lower($string)); // выведет 'привет мир'
```
> См. также [`upper()`](#upper).

---

### `lowerFirst()`
```php
str::lowerFirst(string $string): string
```
Возвращает строку, в который первый символ переведен в нижний регистр. 

```php
$string = 'GameDev';

alert(str::lowerFirst($string)); // выведет 'gameDev'.
```
> См. также [`upperFirst()`](#upperfirst).

---

### `upper()`
```php
str::upper(string $string): string
```
Конвертирует все символы строки `$string` в верхний регистр и возвращает её.
```php
$string = 'HelloWorld';

alert( str::upper($string) ); // выведет 'HELLOWORLD'.
```
> См. также [`lower()`](#lower).

---

### `upperFirst()`
```php
str::upperFirst(string $string): string
```
Возвращает строку, в который первый символ переведен в верхний регистр. 

```php
$string = 'gameDev';

alert(str::lowerFirst($string)); // выведет 'GameDev'.
```
> См. также [`lowerFirst()`](#lowerfirst).

---

### `length()`
```php
str::length(string $string): int
```
Возвращает длину строки, т.е. количество символов внутри строки.

```php
$string = 'develnext';

$len = str::length($string);

alert("Число символов в названии develnext = $len");
```

---

### `replace()`
```php
str::replace(string $string, string $target, string $replacement): string
```
Возвращает строку из `$string`, в которой были заменены все вхождения строки `$target` на строку `$replacement`.

```php
$string = 'develnext';

$newString = str::replace($string, 'next', 'studio');
alert($newString); // выведет 'develstudio'.
```

---

### `repeat()`
```php
str::repeat(string $string, int $amount): string
```
Формирует с помощью `$amount` повторений новую строку из `$string`.

```php
$string = 'hello!';

alert(str::repeat($string, 3)); // выведет hello!hello!hello!
```

---

### `trim()`
```php
str::trim(string $string, string $charList = "\t\n\r\v\0 "): string
```
Обрезает пустые символы из `$charList` слева и справа от строки `$string`.

> По-умолчанию пустыми символами являются `\t` - таб, `\n` и `\r` символы переноса строки, `\0` - нулевой символ и пробел.

```php
$string = '  DevelNext  ';

// выведет просто DevelNext без пробелов справа и слева.
alert(str::trim($string)); 
```

---

### `trimRight()`
```php
str::trimRight(string $string, string $charList = "\t\n\r\v\0 "): string
```
Обрезает пустые символы из `$charList` справа от строки `$string`.

> По-умолчанию пустыми символами являются `\t` - таб, `\n` и `\r` символы переноса строки, `\0` - нулевой символ и пробел.

> См. также [`trim()`](#trim).

---

### `trimLeft()`
```php
str::trimLeft(string $string, string $charList = "\t\n\r\v\0 "): string
```
Обрезает пустые символы из `$charList` слева от строки `$string`.

> По-умолчанию пустыми символами являются `\t` - таб, `\n` и `\r` символы переноса строки, `\0` - нулевой символ и пробел.

> См. также [`trim()`](#trim).

---

### `reverse()`
```php
str::reverse(string $string): string
```
Переворачивает строку `$string`.

```php
$string = 'Hello';

// выведет 'olleH'
var_dump( str::reverse($string) );
```

---

### `shuffle()`
```php
str::shuffle(string $string): string
```
Возвращает исходную строку `$string`, в которой все символы перемешаны в случайном порядке.

> См. также [`random`](#random).

---

### `random()`
```php
str::random(int $length = 16, $set = 'qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM0123456789'): string
```
Возвращает случайную строку длиной `$length`, составленную из набора символов `$set`. По-умолчанию, если ничего не передать, вернет строку из 16 символов из латинского алфавита и цифр. 

```php
$randString = str::random();
$randString = str::random(8);
$randString = str::random(5, 'ABCDFE123');
```

> См. также [`shuffle`](#shuffle).

---

### `split()`
```php
str::split(string $string, string $separator, $limit = 0)
```
Разбивает строку `$string` на массив с помощью строки-разделителя `$separator`. Эквивалент `explode()`. Можно указать максимум разбиений через `$limit`, `0` - означает отсутствие максимума.

```php
$str = 'car,air,hotel';

// выведет array('car', 'air', 'hotel')
print_r(str::split($str, ','));

// выведет array('car', 'air,hotel')
print_r(str::split($str, ',', 2));
```

---

### `join()`
```php
str::join(Iterator|array $iterable, string $separator, int $limit = 0): string
```
Соединяет все элементы массива или итератора `$iterable` в строку через разделитель `$separator`. Эквивалент `implode()`, за исключением того, что еще умеет работать с любыми итерируемыми объектами.

```php
$array = ['car', 'air', 'hotel'];

// выведет 'car--air--hotel'
print_r(str::join($array, '--'));
```

---

### `encode()`
```php
str::encode(string $string, string $charset): string
```
Кодирует строку `$string` в нужную кодировку `$charset`, на выходе обычно получается бинарная строка. Выходит, что метод кодирует строку из родной кодировки jphp для строк в другую. `$charset` может быть `windows-1251` или любое другое название кодировки.

----

### `decode()`
```php
str::decode(string $string, string $charset): string
```
Декодирует бинарную строку `$string` из кодировки `$charset` в родную кодировку строк в jphp. 

---

### `format()`
```php
str::format(string $format, ...$args): string
```
Форматирует строку в формате `$format` с аргументами `$args`. В формате можно указать переданные аргументы через специальное выражение `%s`.

```php
$format = 'Привет, %s, это я, твоя %s';

$string = str::format($format, 'Мир', 'Судьба');
alert($string); // выведет 'Привет, Мир, это я, твоя Судьба'
```

---

### `uuid()`
```php
str::uuid(string $value = null): string
```
Возвращает случайный UUID идентификатор или от строки `$value`. UUID это строка примерно такого вида: `123e4567-e89b-12d3-a456-426655440000`, см. подробнее здесь: [https://ru.wikipedia.org/wiki/UUID](https://ru.wikipedia.org/wiki/UUID).

---

### `hash()`
```php
str::hash(string $string, string $algorithm = 'SHA-1'): string
```
Возвращает хеш строки `$string`, по-умолчанию SHA-1. Алгоритм можно менять через аргумент `$algorightm`.

```php
$sha1 = str::hash('develnext');
$md5 = str::hash('develnext', 'MD5');
$md2 = str::hash('develnext', 'MD2');
$sha256 = str::hash('develnext', 'SHA-256');
$sha512 = str::hash('develnext', 'SHA-512');
```

---

### `lines()`
```php
str::lines(string $string, bool $removeEmpty = false): array
```
Разбивает строку `$string` с помощью символа разделителя "перехода на новую строку" `\r` и `\n`. 

```php
$string = "Строка\nНовая строка\nЕще новая строка";

print_r(str::lines($string));
/*
Выведет:
array (
    "Строка", "Новая строка", "Еще новая строка"
)
*/
```