# PHP API

> Раздел с описанием стандартных классов php и jphp, не относящихся конкретно к интерфейсу приложений.

---

#### Как работать с документацией по API?
> _Если вы хотите более эффективно понимать, что написано в этой документации, прочитайте небольшое описание [**здесь**](API_Manual). Особенно это будет полезно для тех, кто не знает английский язык, а английские слова встречаются в данной документации._

---

#### Базовая информация
- [Язык PHP](Язык-PHP)
- [Автозагрузка классов](api/ClassLoading)
- [Система пакетов в jphp](api/PackageSystem)

#### Примитивные данные
- [str](api/str) - работа с текстом и строками.
- [arr](api/arr) - работа с массивами и итераторами.
- [char](api/char) - работа с текстовыми символами.
- [bin](api/bin) - работа с бинарными данными, бинарными строками.
- [reflect](api/reflect) - работа с рефлексией, данные о типах.
- [fs](api/fs) - работа с файлами и папками.

#### Время и дата
- [Time](api/Time) - класс для времени и даты.
- [TimeZone](api/TimeZone) - временная зона.
- [TimeFormat](api/TimeFormat) - форматирование и парсинг даты и времени.

#### Файлы, IO, потоки данных.
- [fs](api/fs) - утилитный класс для работы с файловой системой.
- [File](api/File) - файл или директория.
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