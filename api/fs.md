# Класс `fs`

- **class** `fs` (`php\lib\fs`).
- **package** `std`

```php
use php\lib\fs;
// или
use std;
```
Утилитный класс для работы с файловой системой, с папками и файлами.

---

#### Статичные методы

- `fs ::`[`isFile()`](#isfile)
- `fs ::`[`isDir()`](#isdir)
- `fs ::`[`size()`](#size)
- `fs ::`[`time()`](#time)

---

### `isFile()`
```php
fs::isFile($path): bool
```
Метод возвращает `true`, если переданный путь `$path` существует и является файлом.

```php
if (fs::isFile('path/to/file.txt')) {
    alert('Файл существует');
}
```

---

### `isDir()`
```php
fs::isDir($path): bool
```
Метод возвращает `true`, если переданный путь `$path` существует и является директорией (папкой).

```php
if (fs::isDir('path/to/')) {
    alert('Папка существует');
}
```

---

### `size()`
```php
fs::size(string $filePath): int
```
Метод возвращает модуль размер файла `$filePath` в байтах. 1 КБ = 1024 байт, 1 МБ = 1024 КБ и т.д.
Если файл не существует, метод вернет `-1`.

---

### `time()`
```php
fs::time(string $path): int
```
Метод возвращает время последнего изменения файла в unix timestamp (в миллискундах).

```php
$time = fs::time('path/to/file.txt');

$time = new Time($time);

// форматирование даты
alert($time->toString('dd-MM-yyyy HH:mm:ss'));
```