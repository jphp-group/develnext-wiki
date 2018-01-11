# Интернет и сеть

- [Как сделать простой GET запрос?](#get-request)
- [Как сделать GET запрос по ссылке и получить JSON?](#get-json)
- [Как определить есть ли у пользователя интернет?](#check-inet)
- [Как загрузить картинку из интернета?](#get-image)
- [Как запросить содержимое по ссылке в нужной кодировке?](#get-content)
- [Как загрузить текстовый файл из интернета?](#get-text-file)

---

<a name=get-request />

## Как сделать простой GET запрос?
> Несколько просты способ сделать GET запрос к http ссылке, сайту.

Для этого вы можете использовать класс `php\io\Stream` или `file_get_contents`, это самые простые способы:

```php
use php\io\Stream;

$content = Stream::getContents('http://develnext.org/');
```

Или вариант с обработкой ошибок:

```php
use php\io\Stream;
use php\io\IOException;

try {
   $content = Stream::getContents('http://develnext.org/');
} catch (IOException $e) {
   alert('Ошибка, сайт недоступен');
}
```

---

<a name=get-json />

## Как сделать GET запрос по ссылке и получить JSON?
> Описание того, как сделать запрос к ссылке, которая отдает json данные.

Вы можете использовать класс `php\io\Stream` и json функции для парсинга данных, далее приведен более правильный код, который учитывает возможность возникновения ошибки при обращении к сайту.

```php
use Exception;
use php\io\Stream;
use php\format\JsonProcessor;

try {
   $parser = new JsonProcessor(JsonProcessor::DESERIALIZE_AS_ARRAYS);

   $data = Stream::getContents('http://example.com/api/json');
   $json = $parser->parse($data);
   pre($json);
} catch (Exception $e) {
   alert('Ошибка');
}
```

Если для вас этот код слишком сложен, то вы можете игнорировать ошибки и использовать старое апи:

```php
$data = file_get_contents('http://example.com/api/json');
$json = json_decode($data, true);

pre($json);
```

---

<a name=check-inet />

## Как определить есть ли у пользователя интернет?
> Описание нескольких нетривиальных методов.

#### Простой способ

Это запросить данные с известного сайта:

```php
$inetEnabled = file_get_contents('http://ya.ru') !== false;

if ($inetEnabled) {
    alert('Интернет есть.');
} else {
    alert('Скорее всего интернета нет.');
}
```

> Для проверки интернета в этом примере используется сайт яндекса, но вы можете использовать любой другой популярный сайт, в котором уверены больше.

---

<a name=get-image />

## Как загрузить картинку из интернета?
> Несколько простых методов загрузки картинки по http ссылке.

Чтобы скачать картинку, да и вообще любой файл, используйте класс `php\lib\fs` и его метод `copy`. Этот метод копирует файл из любого источника, в том числе и из ссылки:

```php
use php\lib\fs;

// откуда копируем, в какой файл
fs::copy('http://develnext.org/assets/img/main_512x512-32.png', 'pic.png');
```

> Код выше, копирует (скачивает) изображение в файл `pic.png` рядом с программой. Вы можете указать и полный путь - куда надо сохранять картинку-файл.

---

<a name=get-content />

## Как запросить содержимое по ссылке в нужной кодировке?
> Простой способ получить содержимое сайта через get запрос в нужной кодировке.

Скорее всего вам подойдет простой метод:

```php
use php\lib\fs;

$news = fs::get('http://site.com/news.txt', 'windows-1251');
alert($news);
```

> Метод декодирует полученный контент из объявленной кодировки в кодировку, которую использует DevelNext (юникод). В этом примере ссылка, например, отдается в кодировке `windows-1251`, но DN использует другую.

Метод можно использовать без кодировки:

```php
$content = fs::get('http://develnext.org');
```

> `fs::get` это аналог функции `file_get_contents` и `Stream::getContents`, он короче и удобнее в использовании и поддерживает возможность указать кодировку источника.

---

<a name=get-text-file />

## Как загрузить текстовый файл из интернета?

Для этого используйте класс `php\io\Stream` или функции `file_get_contents` и `file_put_contents`:

```php
use php\io\Stream;

$url = 'http://mysite.com/file.txt';

try {
   $content = Stream::getContents($url);
   Stream::putContents('file.txt', $content);
} catch (IOException $e) {
   alert('Ошибка скачивания.');
}
```

#### Простой способ

```php
use php\lib\fs;

fs::copy('http://mysite.com/file.txt', 'file.txt');
```

Метод `fs::copy` копирует из любого источника в файл, в данном примере в файл `file.txt`, который находится рядом с программой.
