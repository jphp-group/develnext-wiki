# API

> Реестр всех основных классов, описание их методов и свойств.

---

#### Как работать с документацией по API?
> _Если вы хотите более эффективно понимать, что написано в этой документации, прочитайте небольшое описание [**здесь**](API_Manual). Особенно это будет полезно для тех, кто не знает английский язык, а английские слова встречаются в данной документации._

---

#### [PHP API](PHP-API)
> Описание стандартных классов и функций в php и jphp.

#### Системные
- [UXList](UXList) - список значений.
- [UXImage](UXImage) - изображение, картинка.
- [UXColor](UXColor) - цвет.
- [UXScreen](UXScreen) - экран пользователя.
- [UXTooltip](UXTooltip) - всплывающая подсказка.
- [UXFont](UXFont) - шрифт. 
- [UXClipboard](UXClipboard) - работа с буфером обмена.

#### Вспомогательные
- [Animation](Animation) - анимация для элементов интерфейса.
- [Score](Score) - класс для реализации системы счета, в основном в играх.
- [Geometry](Geometry) - класс для работы с примитивными геометрическими фигурами.
- [Media](Media) - класс для работы с аудио и видео, для воспроизведения медиа-контента.

#### GUI Компоненты
- [UXNode](UXNode) - базовый класс всех gui компонентов.
 - [UXParent](UXParent) > [UXRegion](UXRegion) > [UXControl](UXControl)
- [UXLabeled](UXLabeled) - текстовые компоненты с иконкой.
 - <img align=top src=https://cloud.githubusercontent.com/assets/1113915/22550186/fbd17720-e95f-11e6-8786-eb48ef061916.png> [UXButton](UXButton) - обычная кнопка.
 - <img align=top src=https://cloud.githubusercontent.com/assets/1113915/22552153/c51aa54a-e968-11e6-9157-4153014038fd.png> [UXFlatButton](UXFlatButton) - плоская кнопка.
 - <img align=top src=https://cloud.githubusercontent.com/assets/1113915/22553003/30707f10-e96c-11e6-8912-5b2195295490.png> [UXToggleButton](UXToggleButton) - кнопка-переключатель.
 - <img align=top src=https://cloud.githubusercontent.com/assets/1113915/22618547/46438f0a-eaf0-11e6-8e88-689f576cb5b6.png> [UXLabel](UXLabel) - текст.
 - <img align=top src=https://cloud.githubusercontent.com/assets/1113915/23369179/8d17bd96-fd21-11e6-8115-54e6a64c63df.png> [UXHyperlink](UXHyperlink) - ссылка.
- [UXTextInputControl](UXTextInputControl) - компоненты для ввода текста.
- <img align=top src=https://cloud.githubusercontent.com/assets/1113915/23470109/9b7f01a0-feb6-11e6-8e6b-4b6915bc5214.png>  [UXTextField](UXTextField) - поле ввода.
- <img src="https://cloud.githubusercontent.com/assets/1113915/22550060/51eff8da-e95f-11e6-938b-ea2deb34aa2b.png" align="top" /> [UXListView](UXListView) - список.

