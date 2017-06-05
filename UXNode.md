# UXNode

- **class** `UXnode` (`php\gui\UXNode`)
- **package** `gui`

> Классы наследники:

> [`UXParent`](UXParent), [`UXCanvas`](UXCanvas), [`UXImageView`](UXImageView)

Базовый класс для всех визуальных компонентов в DevelNext. От этого класса наследуются кнопки, тексты, списки и все остальное. Это означает, что все визуальные компоненты имеют методы и свойства описанные ниже!

#### Свойства
- Системные
    - [id](#id-string), [parent](#parent-uxparent), [scene](#scene-uxscene), [form](#form-uxform),  [window](#window-uxwindow), [userData](#userdata-mixed)
- Внешний вид
  - [style](#style-string), [effects](#effects-uxeffectpipeline), [clip](#clip-uxnode), [classes](#classes-uxlist), [classesString](#classesstring-string), [visible](#visible-bool), [enabled](#enabled-bool), [opacity](#opacity-double), [rotate](#rotate-double), [cursor](#cursor-string--uximage)
- Позиция и размеры
  - [x](#x-double), [y](#y-double), [position](#position-array), [screenX](#screenx-double), [screenY](#screeny-double), [translateX](#translatex-double), [translateY](#translatey-double), [translateZ](#translatez-double), [width](#width-double), [height](#height-double), [size](#size-array), [scaleX](#scalex-double), [scaleY](#scaleY-double), [layoutBounds](#layoutbounds-array), [boundsInParent](#boundsinparent-array), [managed](#managed-bool)
- Другое
  - [mouseTransparent](#mousetransparent-bool), [focused](#focused-bool), [focusTraversable](#focustraversable-bool)

#### Методы
- [Конструктор](#__construct) `__construct`
- Системные
  - [data()](#data), [free()](#free), [isFree()](#isfree), [lookup()](#lookup), [lookupAll()](#lookupall)
- Внешний вид
  - [relocate()](#relocate), [resize()](#resize), [hide()](#hide), [show()](#show), [toggle()](#toggle), [toFront()](#tofront), [toBack()](#toback), [requestFocus()](#requestfocus), [snapshot()](#snapshot), [screenToLocal()](#screentolocal)
- События
  - [on()](#on), [off()](#off), [trigger()](#trigger), [observer()](#observer)
- Другое
  - [startFullDrag()](#startfulldrag), [startDrag()](#startdrag)


---

Доступ к свойствам компонента выполняется следующим образом:

```php
$var = $button->id; // id - это свойство компонента от класса UXNode.
// или
$var = $this->button->id;

// для изменения свойства достаточно следующего:
$this->button->id = 'new_value';
```

---

## Свойства

### `id` (string)
Идентификатор.

---

### `style` (string)
CSS стили компонента в одну строку.

---

### `parent` ([UXParent](UXParent))
Родительский компонент.

---

### `effects` ([UXEffectPipeline](UXEffectPipeline))
Эффекты компонента.

---

### `clip` ([UXNode](UXNode))
Компонент, по очертанию которого обрезается текущий компонент, по-умолчанию `null`.

---

### `scene` ([UXScene](UXScene))
Сцена, на которой находится компонент.

---

### `form` ([UXForm](UXForm))
Форма, на которой находится компонент.

---

### `window` ([UXWindow](UXWindow))
Окно, на котором находится компонент.

---

### `x` (double)
Позиция по оси X (горизонтальная).

---

### `y` (double)
Позиция по оси Y (вертикальная).

---

### `position` (array)
Массив [x, y], позиция по x и y.

```php
$button->position = [10, 30]; // 10 - x, 30 - y

list($x, $y) = $button->position;
```

---

### `translateX` (double)
Смещение по X от начального значения.

---

### `translateY` (double)
Смещение по Y от начального значения.

---

### `translateZ` (double)
Смещение по Z от начального значения.

---

### `scaleX` (double)
Масштабирование по X, в процентах от 0 до 1 и выше.

```php
$button->scaleX = 2.0; // растянуть кнопку в 2 раза, 200% - от начального размера.
```

---

### `scaleY` (double)
Масштабирование по Y, в процентах от 0 до 1 и выше.

---

### `screenX` (double)
Абсолютная позиция компонента по X (горизонтали) на экране.

---

### `screenY` (double)
Абсолютная позиция компонента по Y (вертикали) на экране.

---

### `width` (double)
Ширина компонента.

---

### `height` (double)
Высота компонента.

---

### `size` (array)
Размеры компонента [width, height] в виде массива.

```php
$button->size = [100, 30]; // ширина 100, высота 30

list($width, $height) = $button->size;
```

---

### `visible` (bool)
Видимость компонента, по-умолчанию `true`.

---

### `managed` (bool)
Учитывать ли размеры компонента при расчете в различных лэйаутах (layout), по-умолчанию `true`.

---

### `enabled` (bool)
Доступность компонента, по-умолчанию `true`.

---

### `opacity` (bool)
Полупрозрачность компонента, от 0 до 1, где 0 - полная невидимость, 1 - полная непрозрачность. По-умолчанию `1.0`.

```php
$button->opacity = 0.7; // 70% от видимости объекта.
```

---

### `rotate` (double)
Угол наклона компонента, от 0 до 360 градусов, по-умолчанию `0`.

---

### `focused` (bool)
> **Только для чтения**

Стоит ли на компоненте фокус, да - `true`, нет - `false`.

---

### `focusTraversable` (bool)
Доступность фокусировки через клавишу `tab`, по-умолчанию `true`.

---

### `classes` ([UXList](UXList))
Список css классов для применения JavaFX стилей.

```php
$button->classes->add('my-button');
```

---

### `classesString` (string)
Список css классов в виде одной строки, а не UXList, где все классы отделены между собой пробелом.

```
$button->classesString = 'my-button other-class';
```

---

### `userData` (mixed)
Любые пользовательские данные, которые необходимо хранить внутри компонента. См. также метод `data()`.

```php
$button->userData = 'my data string';
$button->userData = ['abcd', 'xyz', 3478];
```

> Свойство может хранить любые значения - строки, числа, массивы, объекты и т.д.

---

### `mouseTransparent` (bool)
Игнорирование действий курсора, по-умолчанию `false`. Если опция включения, компонент перестанет реагировать на любые клики мышкой, хотя останется видимым и реагирующим на другие события.

---

### `cursor` (string / [UXImage](UXImage))
Курсор при наведении на компонент, по-умолчанию `DEFAULT`. Либо строка (символьный код курсора), либо изображение (UXImage) - изображение курсора.

---

### `layoutBounds` (array)
> **Только для чтения**

Размеры и позиция компонента внутри его лэйаута (layout), массив вида:

```php
['x' => 0.0, 'y' => 0.0, 'z' => 0.0, 'width' => 0.0, 'height' => 0.0, 'depth' => 0.0]
```

---

### `boundsInParent` (array)
> **Только для чтения**

Размеры и позиция компонента относительно его родительского компонента, массив вида:

```php
['x' => 0.0, 'y' => 0.0, 'z' => 0.0, 'width' => 0.0, 'height' => 0.0, 'depth' => 0.0]
```

---

## Методы

### `__construct()`
Конструктор компонента, не имеет параметров, публичный.

---

### `data()`
```php
data(string $name[, mixed $value]): mixed
```
Метод для хранения и получения пользовательских данных из компонента. Позволяет хранить любые данные, связанные с компонентов. 

> При использовании метода `data()`, свойство `userData` будет перезаписано и очищено.

```php
// запись данных
$button->data('key', 'my value');

// получение данных
$value = $button->data('key');
```

---

### `screenToLocal()`
```php
screenToLocal(double $x, double $y): array
```
Переводит координаты (x, y) из абсолютных (экранных) в локальные. Возвращает массив координат `[x, y]`.

---

### snapshot()
```php
snapshot(): UXImage
```
Делает скриншот компонента и возвращает его в виде картинки объекта [UXImage](UXImage).

---

### lookup()
```php
lookup(string $selector): UXNode
```
Ищет первый компонент среди содержимого по css селектору и возвращает его. Если ничего не найдено, возвращает `null`.

---

### `lookupAll`
```php
lookupAll($selector): UXNode[]
```
Ищет все компоненты среди содержимого по css селектору и возвращает их. Если ничего не найдено, возвращает пустой массив.

---

### `resize()`
```php
resize(double $width, double $height)
```
Меняет ширину и высотку компонента. См. также свойство [`size`](#size-array).

---

### `relocate()`
```php
relocate(double $x, double $y)
```
Меняет позицию (x, y) компоненту. См. также свойство [`position`](#position-array).

---

### `toFront()`
Переместить компонент поверх всех объектов.

---

### `toBack()`
Переместить компонент под все объекты.

---

### `requestFocus()`
Перевести фокус на объект.

---

### `hide()`
Скрыть объект, см. также свойство [`visible`](#visible-bool).

---

### `show()`
Показать объект, см. также свойство [`visible`](#visible-bool).

---

### `toggle()`
Показать объект если он скрыт и скрыть объект если он отображается, см. также свойство [`visible`](#visible-bool).

---

### `isFree()`
```php 
isFree(): bool
```
Возвращает true, если объект не находится ни на каком другом объекте.

---

### `free()`
Уничтожить объект, удалить его с родительского компонента.

---

### `startFullDrag()`
Начать полную процедуру drag-n-drop для компонента.

---

### `startDrag()`
```php
startDrag(array $modes): UXDragboard
```
Начать процедуру drag-n-drop для компонента в различных режимах работу `$modes`. `$modes` это массив строк, режимы могут быть следующих видов:

- `MOVE` - перемещение
- `COPY` - копирование
- `LINK` - связывание

Метод возвращает объект [UXDragboard](UXDragboard).

---

### `on()`
```php
on(string $event, callable $handler, $group = 'general')
```
Метод добавляет функцию-слушатель `$handler` на определенное событие `$event` компонента. Также можно указать `$group` - символьный код функции-слушателя, под каждым таким кодом может располагаться только одна функция-слушатель, поэтому повторный вызов `on()` с одинаковым значением `$group` перезапишет слушателя события.

```php
$button->on('click', function ($e) {
    alert('Привет мир');
});
```

---

### `off()`
```php
off(string $event[, string $group])
```
Отключить функцию-слушателя от события компонента. Если передать `$group`, то будет отключена лишь одна функция-слушатель под этим символьным кодом.

---

### `trigger()`
```php
trigger($event[, UXEvent $e])
```
Вызвать на выполнение все функции-слушатели определенного события компонента.

---

### `observer()`
```php
observer(string $property): UXValue
```
Добавляет слушателя на изменение определенного свойства компонента. Не на все свойства компонента можно добавить слушателя.

```php
// при изменении видимости компонента.
$button->observer('visible')->addListener(function($oldValue, $newValue) {
    alert("Старое значение = $oldValue \nНовое значение = $newValue");
});
```