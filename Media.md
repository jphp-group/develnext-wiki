# Media

- **class** `Media` (`action\Media`)
```php
use action\Media;
```

Утилитный класс только со статичными методами, для упрощенной работы с медиа-контентом (аудио и видео).

> У класса приватный конструктор, невозможно создать объект данного класса.

---

#### Статичные методы

- `Media ::`[`open()`](#open)
- `Media ::`[`isStatus()`](#isstatus)
- `Media ::`[`stop()`](#stop)
- `Media ::`[`pause()`](#pause)
- `Media ::`[`play()`](#play)

---

### `open()`
```php
open(string $file, bool $autoPlay = true, string | MediaPlayerScript $id = 'general')
```
Загружает медиа-файл из `$file` и начинает его играть если включена опция `$autoPlay`. В качестве плеера `$id` можно указать символьный код или объект класса [MediaPlayerScript](MediaPlayerScript). У каждого такого плеера свой поток воспроизведения, если вы хотите проигрывать несколько звуков параллельно, то используйте разные плееры `$id`.

```php
// проигрываем музыку в отдельном плеере 'background_sound'
Media::open('path/to/music.mp3', true, 'background_sound');

// проигрываем стартовый звук.
Media::open('path/to/start.wav');

// можно указать объект плеера - модульный компонент.
Media::open('path/to/file.mp3', true, $this->player);
```