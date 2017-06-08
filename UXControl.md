# UXControl

- abstract **class** `UXControl` (`php\gui\UXControl`) **extends** [`UXRegion`](UXRegion).

Абстрактый класс компонентов, у которых может быть всплывающая подсказка и контекстное меню.

> Классы наследники:

> [`UXHTMLEditor`](UXHTMLEditor), [`UXLabeled`](UXLabeled), [`UXListView`](UXListView), [`UXMenuBar`](UXMenuBar), [`UXProgressIndicator`](UXProgressIndicator), [`UXScrollPane`](UXScrollPane), [`UXSeparator`](UXSeparator), [`UXSlider`](UXSlider), [`UXSpinner`](UXSpinner), [`UXSplitPane`](UXSplitPane), [`UXTableView`](UXTableView), [`UXTabPane`](UXTabPane), [`UXTextInputControl`](UXTextInputControl), [`UXTreeView`](UXTreeView).

---

#### Свойства
- `->`[`tooltip`](#tooltip-uxtooltip) - _подсказка_
- `->`[`tooltipText`](#tooltipText) - _текст подсказки_
- `->`[`contextMenu`](#contextmenu) - _контекстное меню_
- См. у класса родителя [`UXRegion`](UXRegion).

#### Методы
- См. у класса родителя [`UXRegion`](UXRegion).

---

## Свойства

### `tooltip` ([UXTooltip](UXTooltip))
Всплывающая подсказка для компонента, объект класса `UXTooltip`, по-умолчанию `null`, что означает отсутствие подсказки.
```php
$button->tooltip = new UXTooltip('Подсказка');
```

---

### `tooltipText` (string)
Всплывающая подсказка только в виде текста (строки).
```php
$button->tooltipText = 'Подсказка';
```

---

### `contextMenu` ([UXContextMenu](UXContextMenu))
Контекстное меню компонента, обычно показывается при клике на компонент правой кнопки мыши. По-умолчанию `null`, но не у всех компонентов, у некоторых есть системное контекстное меню.