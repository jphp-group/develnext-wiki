# Earth API

**Earth API** - это многофункциональный бесплатный REST сервис от разработчиков DevelNext, созданный специально для использования в develnext проектах всеми пользователями нашей среды. Сервис умеет предоставлять разную информацию и выполняет некоторые удобные функции, а также не требует никакой регистрации.

_Он располагается по следующему адресу:_
```
https://api.develnext.org/data/v1/
```
> `v1` - первая версия api

---

### Методы

- [Информация об IP](#ip) (`/data/v1/ip/...`)
- [QR Код (генерация)](#qr-code) (`/data/v1/qr-code/...`)
- [Цитаты и афоризмы](#quote) (`/data/v1/quote/...`)

---

<a name=ip />

## Информация об IP

```
  GET  https://api.develnext.org/data/v1/ip/{ip-address}
```
> `{ip-address}` - можно передать любой ip версии 4 или ключевое слово `current`, чтобы использовать ip от клиента, который сделал запрос.

Метод возвращает следующую информацию об IP:

- hostname - имя хоста, если оно имеется.
- city - город, к которому принадлежит ip.
- country - страна, к которому принадлежит ip.
- continent - код континента, к которому принадлежит ip, например `EU` или `NA`.
- location - временная зона и широта/долгота местоположения по ip.
- postal - почтовый индекс.

Пример запроса и ответа:
```json
GET  https://api.develnext.org/data/v1/ip/108.70.12.107

{
  "ip":"108.70.12.107",
  "hostname":"108-70-12-107.lightspeed.clmasc.sbcglobal.net",
  "city":{
    "id":4575352,
    "name":"Columbia",
    "names":{
      "de":"Columbia",
      "ru":"Колумбия",
      "pt-BR":"Colúmbia",
      "ja":"コロンビア",
      "en":"Columbia",
      "fr":"Columbia",
      "zh-CN":"哥伦比亚",
      "es":"Columbia"
    }
  },
  "country":{
    "id":6252001,
    "iso":"US",
    "name":"United States",
    "names":{
      "de":"USA",
      "ru":"США",
      "pt-BR":"Estados Unidos",
      "ja":"アメリカ合衆国",
      "en":"United States",
      "fr":"États-Unis",
      "zh-CN":"美国",
      "es":"Estados Unidos"
    }
  },
  "continent":"NA",
  "location":{
    "latitude":34.0484,
    "longitude":-81.111,
    "timeZone":"America/New_York",
    "population":null
  },
  "postal":"29210"
}
```

#### Как получить текущий IP?

Вернуть информацию о текущем IP клиента:
```
GET  https://api.develnext.org/data/v1/ip/current

Формат ответа см. выше.
```

---

<a name=qr-code />

## QR Код (генерация)
Метод позволяет сконвертировать любой текст не более `2048` символов в изображение QR кода. Метод возвращает изображение в формате `png` (`image/png`).

```
GET https://api.develnext.org/data/v1/qr-code/generate?text={text}&size={size}
```

_Где параметры:_
- `{text}` - текст для конвертирования (обязательный).
- `{size}` - размер изображения результата QR кодирования, от 64 до 1024 пикселей.

_Варианты кодов ответа:_
- `200` - изображение сгенерированно корректно.
- `400` - если параметры переданы неверно, ответ в виде строки.

> Пример (перейдите по ссылке):
https://api.develnext.org/data/v1/qr-code/generate?text=DevelNext&size=300

---

<a name=quote />

## Цитаты и афоризмы
Следующие методы позволяют получать случайные известные цитаты на заданные темы.

#### Случайная цитата

```
GET https://api.develnext.org/data/v1/quote/random?minRating={?}&subject={?}&tags={?}
```

_Где все параметры не обязательны:_

- `minRating` - минимальный рейтинг цитаты от 0 до 1000+.
- `subject` - тема цитаты
- `tags` - список тегов цитат, разделителем выступает символ `|`.

_Пример запросов_
```
GET https://api.develnext.org/data/v1/quote/random?minRating=10
GET https://api.develnext.org/data/v1/quote/random?tags=свобода
GET https://api.develnext.org/data/v1/quote/random?tags=счастье|свобода
GET https://api.develnext.org/data/v1/quote/random?tags=свобода&minRating=12
GET https://api.develnext.org/data/v1/quote/random?subject=цветы
```

_Пример ответа_
```json
{
  "id":"5916fc7a2f0a0d0abcf3e277",
  "text":"Нет ничего более стимулирующего, чем когда всё идёт не так, как надо. (Нет ничего более стимулирующего, чем дело, где все идет против тебя.)",
  "source":{
    "name":null,
    "author":"Шерлок Холмс",
    "authorType":"Цитируемый персонаж",
    "type":null
  },
  "subject":"мотивация",
  "tags":[
    "стимул",
    "Мотивирующие цитаты"
  ],
  "rating":165
}
```

---

#### Список всех доступных тем
Для того, чтобы получить список всех доступных тем, используйте следующий метод:

> Метод также возвращает статистику каждой темы (количество цитат на тему `count`, минимальный и максимальный рейтинг в данной теме).

```
GET https://api.develnext.org/data/v1/quote/subjects
```

_Пример ответа_
```json
[  
  {  
    "value":"профессия",
    "count":32,
    "minRating":0,
    "maxRating":91
  },
  {  
    "value":"объяснение",
    "count":26,
    "minRating":0,
    "maxRating":161
  },
  {  
    "value":"цветы",
    "count":26,
    "minRating":1,
    "maxRating":272
  },
  {  
    "value":"долг",
    "count":25,
    "minRating":0,
    "maxRating":85
  },
  {  
    "value":"неприятности",
    "count":24,
    "minRating":0,
    "maxRating":191
  },
  {  
    "value":"время",
    "count":24,
    "minRating":0,
    "maxRating":551
  }
]
```

---

#### Список всех доступных тегов
Для того, чтобы получить список всех доступных тегов, используйте следующий метод:

> Метод также возвращает статистику каждого тега (количество цитат `count`, минимальный и максимальный рейтинг в данном теге).

```
GET https://api.develnext.org/data/v1/quote/tags
```


_Пример ответа_
```json
[
  {
    "value":"Жизненные цитаты",
    "count":1121,
    "minRating":-4,
    "maxRating":885
  },
  {
    "value":"Ироничные цитаты",
    "count":678,
    "minRating":-2,
    "maxRating":674
  },
  {
    "value":"Смешные цитаты",
    "count":572,
    "minRating":-2,
    "maxRating":1079
  },
  {
    "value":"Саркастичные цитаты",
    "count":427,
    "minRating":-1,
    "maxRating":434
  },
  {
    "value":"Грустные цитаты",
    "count":388,
    "minRating":0,
    "maxRating":290
  },
  {
    "value":"Мудрые цитаты",
    "count":379,
    "minRating":-2,
    "maxRating":823
  },
  {
    "value":"любовь",
    "count":343,
    "minRating":-1,
    "maxRating":699
  },
  {
    "value":"человек, люди",
    "count":302,
    "minRating":0,
    "maxRating":405
  }
]
```