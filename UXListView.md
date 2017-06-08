# UXListView

- **class** <img src="https://cloud.githubusercontent.com/assets/1113915/22550060/51eff8da-e95f-11e6-938b-ea2deb34aa2b.png" align="top" /> `UXListView` (`php\gui\UXListView`) **extends** [`UXControl`](UXControl).
```php
use php\gui\UXListView;
```

> ![image](https://cloud.githubusercontent.com/assets/1113915/22548733/f102a79e-e958-11e6-8c69-a59221f9ffe6.png)

Класс компонента для отображений списков в GUI, в котором можно выделять элементы.

> Изображение компонента:

> ![image](https://cloud.githubusercontent.com/assets/1113915/22548679/b09d9cae-e958-11e6-8914-adee0cf8c2e3.png)

---

#### Свойства
- `->`[`editable`](#editable-bool)
- `->`[`editingIndex`](#editingindex-int)
- `->`[`fixedCellSize`](#fixedcellsize-double)
- `->`[`placeholder`](#placeholder-uxnode)
- `->`[`items`](#items-uxlist)
- `->`[`itemsText`](#itemstext-string)
- `->`[`orientation`](#orientation-string)
- `->`[`multipleSelection`](#multipleselection-bool)
- `->`[`selectedIndexes`](#selectedindexes-array)
- `->`[`selectedIndex`](#selectedindex-int)
- `->`[`focusedIndex`](#focusedindex-int)
- `->`[`selectedItems`](#selecteditems-array)
- `->`[`selectedItem`](#selecteditem-mixed)
- `->`[`focusedItem`](#focuseditem-mixed)

#### Методы
- [Конструктор (`new`)](#__construct) `__construct`
- `->`[`scrollTo()`](#scrollto)
- `->`[`edit()`](#edit)
- `->`[`setCellFactory()`](#setcellfactory)
- `->`[`setDraggableCellFactory()`](#setdraggablecellfactory)
- `->`[`update()`](#update)

---

## Свойства

### `editable` (bool)
> В разработке, свойство еще не работает.
Возможность редактировать элементы списка двойным кликом или вызовом метода [`edit()`](#edit). По-умолчанию `false`.

---

### `editingIndex` (int)
> Только для чтения.

Индекс элемента, который в данный момент находится на редактировании.

---

### `fixedCellSize` (int)
Размер ячейки, высота каждого элемента в списке, по-умолчанию значение `-1`, которое означает, что высота будет высчитываться автоматически.

![image](https://cloud.githubusercontent.com/assets/1113915/22548914/e3b8a9ca-e959-11e6-974e-ada27a99b7de.png)

---

### `placeholder` ([UXNode](UXNode))
Компонент, который будет отображаться если список пустой. Это может быть что угодно, картинка, кнопка, любой визуальный компонент. По-умолчанию `null`, что означает - при пустом списке ничего не отображать.

```php
$listView->placeholder = new UXLabel('Список пуст.');
```

---

### `items` ([UXList](UXList))
Содержимое списка, набор его элементов. Обычно он состоит из строк, однако это могут быть любые значения - числа, текст, объекты и даже другие визуальные компоненты. 

> По-умолчанию, при отображении списка компонент пытается любое значение привести к строке, в этом случае, для объектов будет вызываться их магический метод `__toString()`. Это поведение можно переопределить через метод [`setCellFactory()`](#setcellfactory).

---

### `itemsText` (string)
Содержимое списке в виде одной строки, в виде текста, где каждая строка отделена символом перевода на новую строку `\n`.
```php
$text = $listView->itemsText;
// это аналогично такому коду
$text = str::join($listView->items, "\n");
```

---

### `orientation` (string)
Направление списка - горизонтальное (`'HORIZONTAL'`) или вертикальное (`'VERTICAL'`), по-умолчанию вертикальное `'VERTICAL'`.

---

### `multipleSelection` (bool)
Возможность выделить в списке сразу несколько элементов, например, зажав кнопку CTRL или SHIFT.

---

### `selectedIndexes` (array)
Массив индексов выделенных элементов в списке, индексация начинается с нуля. Особенно актуально, когда в списке можно выделить несколько элементов.

---

### `selectedIndex` (int)
Выделенный элемент в списке, индексация начинается с нуля. Если значение равно `-1`, значит в списке ничего не выделено.
```php
$listView->selectedIndex = -1; // снимает выделение со всех элементов.
$listView->selectedIndex = 2; // выделить 3 по счету элемент.
```

---

### `focusedIndex` (int)
Индекс элемента из списка, на котором стоит фокус.

---

### `selectedItems` (array)
Список выделенных элементов в списке в виде массива их значений (не путать с индексами). Особенно актуально, когда можно выделять несколько элементов.

---

### `selectedItem` (mixed)
Один выделенный элемент в списке, его значение (не путать с индексами).

---

### `focusedItem` (mixed)
Элемент, его значение, на котором стоит фокус (не путать с индексами).

---

## Методы

### `__construct()`
Конструктор класса UXList, без параметров.
```php
$listView = new UXListView();
```

---

### `scrollTo()`
```php
scrollTo(int $index)
```
Проскролить к элементу под индексом `$index`, индексация начинается с нуля. См. также [`selectedIndex`](#selectedindex-int) и [`focusedIndex`](#focusedindex-int).

---

### `edit()`
```php
edit(int $index)
```
Начать редактирование элемента под индексом `$index`, индексация начинается с нуля. Не работает без установленного в `true` свойства [`editable`](#editable-bool).

---

### `setCellFactory()`
```php
setCellFactory(callable $handler)
```
где `$handler` это метод или функция вида:
```php
function (UXListCell $cell, mixed $item)
```

Метод переопределяет то, как визуально отображать элементы в списке.

```php
$listView->setCellFactory(function (UXListCell $cell, $item) {
    $cell->graphic = new UXLabel($item->text);
    $cell->text = null;
});
```

---

### `setDraggableCellFactory()`
```php
setDraggableCellFactory(callable $handler, callable $dragDoneHandler)
```
где:
```php
// $handler 
function (UXListCell $cell, $item) {}

// $dragDoneHandler
function (UXDragEvent $e, UXListView $view) {}
```
Определяет то, как будет выглядеть процедура drag-n-drop для списка.

---

### `update()`
Вызывает перерисовку компонента списка, иногда актуально, когда компонент не может зафиксировать обновление [`items`](#items), необходимо вызвать этот метод.