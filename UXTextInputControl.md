# UXTextInputControl

- abstract **class** `UXTextInputControl` (`php\gui\UXTextInputControl`) **extends** [`UXControl`](UXControl).

> Классы наследники:

> [`UXTextField`](UXTextField), [`UXTextArea`](UXTextArea).

Базовый абстрактный класс всех компонентов, предназначенных для ввода текстовой информации.

---

#### Свойства
- `->`[`text`](#text-string)
- `->`[`font`](#font-uxfont)
- `->`[`selection`](#selection-array)
- `->`[`selectedText`](#selectedtext-string)
- `->`[`promptText`](#prompttext-string)
- `->`[`length`](#length-int)
- `->`[`editable`](#editable-bool)

#### Методы
- `->`[`copy()`](#copy)
- `->`[`cut()`](#cut)
- `->`[`paste()`](#paste)
- `->`[`clear()`](#clear)
- `->`[`end()`](#end)
- `->`[`home()`](#home)
- `->`[`forward()`](#forward)
- `->`[`backward()`](#backward)
- `->`[`nextWord()`](#nextword)
- `->`[`previousWord()`](#previousword)
- `->`[`selectAll()`](#selectall)
- `->`[`selectBackward()`](#selectbackward)
- `->`[`selectEnd()`](#selectend)
- `->`[`selectEndOfNextWord()`](#selectendofnextword)
- `->`[`selectForward()`](#selectforward)
- `->`[`selectHome()`](#selecthome)
- `->`[`selectNextWord()`](#selectnextword)
- `->`[`selectPreviousWord()`](#selectpreviousword)
- `->`[`selectPositionCaret()`](#selectpositioncaret)
- `->`[`selectRange()`](#selectrange)
- `->`[`extendSelection()`](#extendselection)
- `->`[`deselect()`](#deselect)
- `->`[`appendText()`](#appendtext)
- `->`[`insertText()`](#inserttext)
- `->`[`replaceText()`](#replacetext)
- `->`[`replaceSelection()`](#replaceselection)
- `->`[`positionCaret()`](#positioncaret)
- `->`[`undo()`](#undo)
- `->`[`redo()`](#redo)
- `->`[`commitValue()`](#commitvalue)
- `->`[`cancelEdit()`](#canceledit)

---

## Свойства

### `text` (string)
Введенный текст.

---

### `font` ([UXFont](UXFont))
Шрифт текста для ввода. 

```php
$field->font = UXFont::of('Tahoma', 16);
```

---

### `selection` (array)
> ⚠️ Только для чтения!

Информация о выделенной области текста компонента, следующего формата:
```php
['start' => 3, 'end' => 10, 'length' => 7]
```
> `start` начальный индекс выделения, `end` - конечный, `length` - длина выделения.

```php
var_dump($field->selection);
```

---

### `selectedText` (string)
Выделенный текст компонента для ввода. Свойство можно как читать, так и менять. При смене значения этого свойства, выделенный текст заменяется на новый.

```php
alert($this->textField->selectedText);

$this->textField->selectedText = 'newText';
```

---

### `promptText` (string)
Текст подсказки для ввода, отображается когда на компоненте нет фокуса и когда текст компонента пустой.