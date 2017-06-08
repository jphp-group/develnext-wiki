# Дата и Время

- [Как получить текущую дату и время?](#now)
- [Как получить текущий год, месяц и день?](#now-y-m-d)
- [Как получить timestamp в linux виде?](#unixtimestamp)
- [Как получить текущее время в другой временной зоне?](#now-timezone)
- [Как получить название месяца даты?](#month-name)
- [Как парсить дату из строки по определенному формату?](#parse)

---

<a name=now />

## Как получить текущую дату и время?
> Информация о том, как получить дату и время в удобном виде.

Для работы со временем используйте специальный класс `php\time\Time`, чтобы получить текущее время и дату используйте код:

```php
use php\time\Time;

$now = Time::now();
alert($now->toString('yyyy-MM-dd HH:mm'));
```

Где формат вывода времени это `yyyy-MM-dd HH:mm`, `y` - это год, `M` - месяц, `d` - день, `H` - час, `m` - минута, `s` - секунда.


> Чтобы вывести только дату используйте формат `yyyy-MM-dd`, например. Можно использовать и другое сочетание, например `dd.MM.yyyy`.

---

<a name=now-y-m-d />

## Как получить текущий год, месяц и день?
> Удобный способ получить текущий год, месяц и день.

Для этого используйте класс `php\time\Time` и его методы:

```php
use php\time\Time;

$now = Time::now(); // получаем текущую дату

$year = $now->year(); // текущий год
$month = $now->month(); // текущий месяц
```

День можно получить в разном контексте:

```php
$day = $now->day(); // день в году, от 1 до 356
$dayOfMonth = $now->dayOfMonth(); // день в месяце, от 1 до 31
$dayOfWeek = $now->dayOfWeak(); // день недели, от 1 до 7, 1 - воскресенье, 7 - суббота.
```

---

<a name=unixtimestamp />

## Как получить timestamp в linux виде?
> Простой способ получить linux timestamp значение времени в системе.

Используйте класс `php\time\Time` или функцию `time()` из php:

```php
use php\time\Time;

$time = Time::seconds(); // в секундах.
$millis = Time::millis(); // в миллисекундах.

// или
$time = time(); // в секундах.
```

> Linux timestamp это количество секунд, прошедших с 1970 года на текущий момент времени.

---

<a name=now-timezone />

## Как получить текущее время в другой временной зоне?
> Применение timezone возможностей для получения текущего времени.

Используйте классы `php\time\Time` и `php\time\TimeZone`:

```php
use php\time\Time;
use php\time\TimeZone;

$now = Time::now(TimeZone::of('Europe/London'));

alert($now->toString('yyyy.MM.dd HH:mm'));
```

> Список возможных временных зон, можно найти на странице "[Временные Зоны (Timezone)](Временные-Зоны-(Timezone))".

---

<a name=month-name />

## Как получить название месяца даты?

```php
$month = 7; // 7 месяц.
$name = Time::now()->replace(['month' => $month])->toString('MMMM');

alert($name);
```

Если вам необходимо получить имя месяца на русском языке, то передайте локаль в метод `toString()`:

```php
$month = 7; // 7 месяц.
$name = Time::now()->replace(['month' => $month])->toString('MMMM', new Locale('ru', 'RU')); // ru - язык, RU - страна

alert($name);
```

> :information_source: Укороченное название месяца можно получить передав `MMM` вместо `MMMM` в метод `toString()`.

---

<a name=parse />

## Как парсить дату из строки по определенному формату?
> Перевод строки в объект даты.

Для парсинга даты из строки используйте класс `php\time\TimeFormat` и его метод `parse()`:

```php
$format = new TimeFormat('dd.MM.yyyy');
$date = $format->parse('12.03.2017');

// $date это объект типа Time 
var_dump($date);
```