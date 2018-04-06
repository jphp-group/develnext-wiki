# UXClipboard

- **class** `UXClipboard` (`php\gui\UXClipboard`)
- **package** `gui`
- **tags** `clipboard`, `cut`, `paste`, `copy`, `буфер`, `буффер`, `буфер обмена`, `копировать`, `вставить`, `вырезать`

```php
use php\gui\UXClipboard;
// или
use gui;
```

Утилитарный класс для работы с буфером обмена системы (функции копирования и вставки в рамках всей ОС). Класс имеет только статичные методы, невозможно создать объект данного класса.

---

#### Статичные методы

- `UXClipboard ::`[`clear()`](#clear) - _очистка буфера_
- `UXClipboard ::`[`getText()`](#gettext) - _получить текст из буфера_
- `UXClipboard ::`[`setText()`](#settext) - _положить текст в буфер_
- `UXClipboard ::`[`setContent()`](#setcontent) - _положить контент в буфер_
- `UXClipboard ::`[`getImage()`](#getimage) - _получить изображение из буфера_
- `UXClipboard ::`[`getFiles()`](#getfiles) - _получить пути к файлам из буфера_
- `UXClipboard ::`[`getHtml()`](#gethtml) - _получить html из буфера_
- `UXClipboard ::`[`getUrl()`](#geturl) - _получить ссылку из буфера_
- `UXClipboard ::`[`hasText()`](#hastext) - _есть ли текст в буфере_
- `UXClipboard ::`[`hasImage()`](#hasimage) - _есть ли изображение в буфере_
- `UXClipboard ::`[`hasFiles()`](#hasfiles) - _есть ли пути к файлам в буфере_
- `UXClipboard ::`[`hasHtml()`](#hashtml) - _есть ли html в буфере_

---

## Статичные методы

### `clear()`
Очистить буфер обмена от любых данных.

```php
// очистка буфера
UXClipboard::clear();
```

---

### `getText()`
```php
UXClipboard::getText(): string
```
Метод возвращает текст из буфера обмена, если его там нет, возвращает `null`.

```php
// показать текст из буфера обмена
alert(UXClipboard::getText());
```

---

### `setText()`
```php
UXClipboard::setText(string $text)
```
Метод помещает текст `$text` в буфер обмена.

```php
// поместить текст в буфер обмена.
UXClipboard::setText('Hello World');
```

> :information_source: Смотрите также метод [`setContent()`](#setcontent).

---

### `setContent()`
```php
UXClipboard::setContent(array $content)
```
Метод помещает разнообразный контент (текст, изображения, файлы и т.д.) в буфер обмена. В массиве `$content` под различными ключами передается нужный контент: `text` для текст, `image` для изображения объект [UXImage](UXImage), `files` для списка путей к файлам в виде массива или итератора, `html` для html, `url` для ссылки.

```php
UXClipboard::setContent([
     'files' => ['path/to/file1.png', 'path/to/file2.png'],
     'text' => 'foobar text',
     'url' => 'http://develnext.org',
     'html' => '<b>World</b>',
     'image' => new UXImage('path/to/image.png')
]);
```

---

### `getImage()`
```php
UXClipboard::getImage(): UXImage
```
Метод возвращает изображения из буфера обмена в виде объекта [UXImage](UXImage).

```php
// загрузить изображения из буфера в компонент изображение.
$this->clipImage->image = UXClipboard::getImage();
```

---

### `getFiles()`
```php
UXClipboard::getFiles(): array
```
Метод возвращает список путей к файлам из буфера обмена. 

> :information_source: Копирование файлов в различных ОС происходит через помещение их полных путей в буфер обмена.

```php
$files = UXClipboard::getFiles();
print_r($files);
```
