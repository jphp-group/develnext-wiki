# PHP API

> Раздел с описанием стандартных классов php и jphp, не относящихся конкретно к интерфейсу приложений.

---

#### Как работать с документацией по API?
> _Если вы хотите более эффективно понимать, что написано в этой документации, прочитайте небольшое описание [**здесь**](API_Manual). Особенно это будет полезно для тех, кто не знает английский язык, а английские слова встречаются в данной документации._

---

#### Базовая информация
- [Язык PHP](Язык-PHP)
- [Автозагрузка классов](ClassLoading)
- [Система пакетов в jphp](PackageSystem)

#### Примитивные данные
- [str](str) - работа с текстом и строками.
- [arr](arr) - работа с массивами и итераторами.
- char - работа с текстовыми символами.
- bin - работа с бинарными данными, бинарными строками.
- [reflect](reflect) - работа с рефлексией, данные о типах.
- [fs](fs) - работа с файлами и папками.

#### Время и дата
- [Time](Time) - класс для времени и даты.
- [TimeZone](TimeZone) - временная зона.
- [TimeFormat](TimeFormat) - форматирование и парсинг даты и времени.

#### Файлы, IO, потоки данных.
- [fs](fs) - утилитный класс для работы с файловой системой.
- [File](File) - файл или директория.
- [Stream](Stream) - базовый класс IO, поток данных.
 - [FileStream](FileStream) - файловый поток данных.
 - [ResourceStream](ResourceStream) - ресурсный поток данных.
 - [MemoryStream](MemoryStream) - RAM поток данных.
 - [NetStream](NetStream) - HTTP, HTTPS, FTP поток данных.
 - [MiscStream](MiscStream) - stdout, stdin и т.п. 

#### Многопоточность (multithreading)
- [Thread](Thread) - поток выполнения кода.
- [ThreadPool](ThreadPool) - пул потоков.
- [ThreadGroup](ThreadGroup) - группа потоков.
- [Shared](Shared)
- [SharedMemory](SharedMemory)
 - [SharedValue](SharedValue)
 - [SharedQueue](SharedQueue)
 - [SharedStack](SharedStack)
 - [SharedMap](SharedMap)