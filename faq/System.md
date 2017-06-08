# Системные утилиты

- [Как получить путь к системной temp папке?](#temp-path)
- [Как получить MAC адрес?](#mac-address)
- [Как получить разрешение экрана?](#screen-size)
- [Как получить название и версию операционной системы?](#osinfo)
- [Как получить имя пользователя системы?](#username)
- [Как получить позицию курсора?](#cursor-pos)
- [Как получить массив всех Environment переменных?](#env)

---

<a name=temp-path />

## Как получить путь к системной temp папке?

Для получения пути к системной temp папки на любой OS используйте код:

```php
use php\lang\System;

$tempDir = System::getProperty('java.io.tmpdir');
```

---

<a name=mac-address />

## Как получить MAC адрес?

Для этого используйте следующий код:

```php
use php\gui\UXApplication;

$macAddress = UXApplication::getMacAddress();
```

> Осторожно, иногда метод возвращает пустое значение, т.к. виртуальная ОС, например, не возвращает никакой mac адрес.

---

<a name=screen-size />

## Как получить разрешение экрана?

Для этого используйте класс `php\gui\UXScreen`:

```php
use php\gui\UXScreen;

$screen = UXScreen::getPrimary();

$width  = $screen->bounds['width'];
$height = $screen->bounds['height'];
```

В этом примере в переменных `$width` и `$height` будет находится ширина и высота экрана пользователя.

---

<a name=osinfo />

## Как получить название и версию операционной системы?

Для этого используйте класс `php\lang\System` и метод `getProperty`:

```php
use php\lang\System;

$osName = System::getProperty('os.name');
$osVersion = System::getProperty('os.version');
```

> В переменной `$osName` будет имя ос, например `Windows`, а в `$osVersion` версия ос.

---

<a name=username />

## Как получить имя пользователя системы?

Используйте класс `php\lang\System` и метод `getProperty`:

```php
use php\lang\System;

$userName = System::getProperty('user.name');
```

> В переменной `$userName` будет находиться имя пользователя.

---

<a name=cursor-pos />

## Как получить позицию курсора?

Есть два способа получить позицию курсора.

#### Первый способ

Используйте модульный компонент `Робот` и его свойства `x` и `y`:

```php
$x = $this->robot->x;
$y = $this->robot->y;

alert("Позиция курсора = $x, $y");
```

#### Второй способ

Используйте утилитный класс `php\desktop\Mouse`:

```php
use php\desktop\Mouse;

$x = Mouse::x();
$y = Mouse::y();
```

---

<a name=env />

## Как получить массив всех Environment переменных?

Для этого используйте класс `php\lang\System` и его метод `getEnv()`:

```php
use php\lang\System;

$env = System::getEnv();

pre($env);
```

Или например одну переменную:

```php
use php\lang\System;

$javaHome = System::getEnv()['JAVA_HOME'];
```

---

Также вы можете использовать и супер-глобальную переменную `$_ENV`, которая содержит массиво-подобный объект (ArrayAccess + Iterator + Countable), например так:

```php
$javaHome = $_ENV['JAVA_HOME'];
```