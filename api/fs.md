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

- `fs ::`[`separator()`](#separator) - _возвращает резделитель для имен файлов_
- `fs ::`[`pathSeparator()`](#pathseparator) - _возвращает разделитель файловых путей_
- `fs ::`[`valid()`](#valid) - _валидно ли имя файла для ОС_
- `fs ::`[`abs()`](#abs) - _абсолютный путь к файлу/папке_
- `fs ::`[`name()`](#name) - _имя файла/папки от полного пути_
- `fs ::`[`nameNoExt()`](#namenoext) - _имя файла без расширения от полного пути_
- `fs ::`[`pathNoExt()`](#pathnoext) - _полный путь без расширения_
- `fs ::`[`ext()`](#ext) - _расширение файла_
- `fs ::`[`hasExt()`](#hasext) - _содержит ли расширение файла_
- `fs ::`[`parent()`](#parent) - _возвращает родительский путь на уровень выше_
- `fs ::`[`ensureParent()`](#ensureparent) - _создает папку для пути, если ее еще нет_
- `fs ::`[`normalize()`](#normalize) - _нормализует внешний вид пути для текущей ОС_
- `fs ::`[`exists()`](#exists) - _существует ли файл или папка_
- `fs ::`[`isFile()`](#isfile) - _путь является ли файлом_
- `fs ::`[`isDir()`](#isdir) - _путь является ли папкой_
- `fs ::`[`isHidden()`](#ishidden) - _скрыт(а) ли файл/папка_
- `fs ::`[`size()`](#size) - _размер файла в байтах_
- `fs ::`[`time()`](#time) - _последнее время изменения файла/папки в миллисекундах (unixstamp)_
- `fs ::`[`makeDir()`](#makedir) - _создать папку_
- `fs ::`[`makeFile()`](#makefile) - _создать пустой файл_
- `fs ::`[`delete()`](#delete) - _удалить файл или пустую папку_
- `fs ::`[`clean()`](#clean) - _очистить папку от всех файлов_
- `fs ::`[`scan()`](#scan) - _просканировать папку_
- `fs ::`[`hash()`](#hash) - _посчтитать хэш файла (MD5, SHA1 и т.д.)_
- `fs ::`[`copy()`](#copy) - _скопировать из потока или файла в другой файл_
- `fs ::`[`move()`](#move) - _переместить файл_
- `fs ::`[`rename()`](#rename) - _переименовать файл_
- `fs ::`[`get()`](#get) - _вернуть содержимое файла в виде строки_

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

---

### `scan()`
```php
fs::scan(string $path, callable|array $filter = null, int $maxDepth = 0, $subIsFirst = false): array
```
> (!) Внимание, фильтр в виде массива и результат добавлен только в версии DN 1.6.1 и выше.

Метод сканирует папку на файлы и папки с помощью фильтра (функция или массив). 

```php
fs::scan('path/to/dir', function (File $file, $depth) {
    echo $file, "\n"; // нашли файл/папку.
});
```

Пример для версии DN 1.6.1+:
```php
$files = fs::scan('path/to/dir'); // найти и вернуть все файлы/папки

// найти файлы только определенных расширений и вернуть.
$files = fs::scan('path/to/dir', ['extensions' => ['jpg', 'png', 'gif', 'jpeg'], 'excludeDirs' => true]); 

// найти все папки и вернуть
$files = fs::scan('path/to/dir', ['excludeFiles' => true]);

// найти все файлы, размер которых больше 10 мб и меньше 100 мб.
$files = fs::scan('path/to/dir', ['minSize' => 1024 * 1024 * 10, 'maxSize' => 1024 * 1024 * 100]);
```

---

### `copy()`
```php
fs::copy(string|Stream $source, string|Stream $dest, callable $onProgress = null, int $bufferSize = 8096): int
```
Метод копирует данные из файла или стрима `$source` в другой файл или стрим `$dest`, при этом используется буффер и все данные не загружаются разом в память. 

Через аргумент `$onProgress` можно навесить функцию-коллбэк для контролирования прогресса копирования данных, а через `$bufferSize` можно регулировать размер буфера. Рекомендуется увеличивать размер буфера до сотен килобайт при копировании огромных данных!

Функция позволяет также копировать и файлы/страницы из интернета и сети.

```php
fs::copy('file.txt', 'fileNew.txt'); // просто копирует файл.

fs::copy('http://example.com/file.txt', 'file.txt'); // копирует файл с сайта.

$stream = new MemoryStream('hello world');
fs::copy($stream, 'file.txt'); // копирует из потока в файл.
```

Функция возвращает количество скопированных байт данных.

---

### `get()`
```php
fs::get(string $source, string $charset = null, string $mode = 'r'): string
```
Метод возвращает контент файла или стрима `$source`, метод похож на функцию `file_get_contents()`.

---

### `ensureParent()`
```php
fs::ensureParent(string $filePath): bool
```
Метод создает папку файла если ее еще нет.
