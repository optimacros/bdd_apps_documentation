
# Basic-шаги (Часто используемые)

## Сервисные шаги

### 1) * Start with an isolated model "ModelName"
Создает копию модели (изолированную модель) и запускает ее.

### 2) * Start with a not isolated model "ModelName"
Запускает оригинальную (не изолированную) модель.

### 3) * Start as a "User"
Запускает приложение с правами доступа определенного пользоваля, например: Modeller, Developer, Not Modeller.

### 4) * Delete the current model
Удаляет ранее созданную копию модели (изолированную модель).

***Нужно быть осторожным, если вы запустите тест в оригинальной модели, то шаг удалит вашу модель!***

### 5) * Go to page Drive Landing
Открывает страницу Drive Landing.

### 6) * Go to page Contents Page
Открывает страницу Contents Page.

### 7) * Open tab "ModuleName"
Переходит на страницу Contents и открывает вкладку с указанным именем.

### 8) * Reload Page
Перезагружает страницу.

### 24) * Wait until the modal form is open
Ожидает открытие модального окна.

## Проверка существования элементов

### 9) * Check if the Grid exists and loaded
Шаг проверят загрузку грида и отсуствие лоадера. Часто применяется после открытия нового грида или изменения состояния грида на котором находится пользователь. Когда заведомо известно, что грид должен загрузиться или обновиться, то применяем этот шаг. Можно не применять его если мы проверяем какие-то элементы в гриде. Например мы вошли в новый грид, проверили существование колонки с определенным названием или строки и это гарантирует нам что грид загружен, иначе элементов видно небыло-бы без загрузки грида.

__*Мне не нравится это описание - много текста. Подумай как убрать лишнее.*__

### 10) * Check if "Selector" exists
Проверяет существование элемента на странице.
```
* Check if "Modal" exists
* Check if "Row Header(Балтика)" exists
* Check if "Any Loader" exists
```

### 11) * Check if "Selector" does not exist
Проверяет отсутствие элемента на странице.
```
* Check if "Modal" does not exist
* Check if "Row Header(Балтика)" does not exist
* Check if "Any Loader" does not exist
```

Важно перед таким шагом проверять существование других элементов или завершение загрузки грида
```
* Check if the Grid exists and loaded
* Check if "Row Header(1:-1)" does not exist
```
 или 

 ```
* Click on "Menu Item(Hide) > Menu Item(All Entries)"
* Check if the Grid exists and loaded
* Check if "Row Header(Толстяк)" exists
* Check if "Row Header(Балтика)" does not exist
```

### 12) * Check if "Selector" contains "Text"
Проверяет что элемент содержит текст.
```
* Check if "Modal > Sample Value" contains "-1,234.56789"
```
Проверяет что в модальном окне есть текст `-1,234.56789`.

### 13) * Check if "Selector" does not contain "Text"
Проверяет что элемент не содержит текст.

### 14) * Check if "Selector" attribute value equals to "Value"
Проверяет значение в инпуте.
```
* Check if "Modal > Input(dependOn)" attribute value equals to "1.2 Контрагенты"
```

### 15) * Check if "Selector" property value equals to "Value"
Проверяет свойство property у определенного элемента.
```
* Check if "Grid Cell Editor" property value equals to "VCAR_01_01"
```

### 16) * Check if the property value for "CollName" and "RowName" equals to "Value"
Проверяет значение в ячейке на пересечении строки и колонки с именами.
```
* Check if the property value for "О1.2" and "Text col with data" equals to "444"
```
- Первый аргумент О1.2 - название колонки
- Text col with data - название строки. 
- 444 - данные в ячейке

### 17) * Check if the elements in the grid match:
Проверяет что грид содержит значения.
```JavaScript 
* Check if the elements in the grid match:
    | 0:-1 | cube 1 | 21 | 17 |
    | 1:-1 | cube 2 |  2 | В2 |
```
Шаг проверяет данные в гриде, с указанием номера строки и данных в колонках. Колонки отбиваются друг от друга символом **|** 

Есть возможность не указывать значения клеток **|  |** оставить контейнер пустым

### 18) * Check if the elements in the grid do not match:
Проверяет что грид содержит значения.
```JavaScript 
* Check if the elements in the grid do not match:
    | 0:-1 | cube 1 | 21 | 17 |
    | 1:-1 | cube 2 |  2 | В2 |
```

### 18) * Check if the elements in context ""DashboardSelector"" grid match:
Проверяет что грид в карточке дашборда содержит значения.
```JavaScript 
* Check if the elements in context ""DashboardSelector"" grid match:
  | 0:-1 | Value | Value | Value |
  | 1:-1 | Value | Value | Value |
```
### 18) * Check if the elements in context "DashboardSelector" grid do not match:
Проверяет что грид в карточке дашборда не содержит значения.
```JavaScript 
* Check if the elements in context "DashboardSelector" grid do not match:
  | 0:-1 | Value | Value | Value |
  | 1:-1 | Value | Value | Value |
```

### 19) * Сheck if the input value in "Selector" equals to "Value"
Проверяет что введенный в поле ввода текст равен значению.

### 22) * Check if "Selector" with text "Text" is active
Проверяет что вкладка с названием “Text” активна.
```
* Check if "Tab Header" with text "Half Years" is active
```

### 23) * Check if "Selector" with text "Text" is not active
Проверяет что вкладка с названием “Text” не активна.
```
* Check if "Tab Header" with text "Half Years" is not active
```

## Работа с Инпутами

### 25) * Clear value in "Selector"
Очищает значения в поле input. В качестве аргумента указывается атрибут Name нужного input.
```
* Clear value in "Conditional Formatting(Maximum) > Input"
```

### 27) * Type "Text" into "Selector"
Печатает текст в инпуте.
```
* Type "20" into "Input(fontSize)"
```
___Вообще не понятно что тут написано. Нужно перефразировать!!!!!___
Шаг введет данные в поле ввода(Input) с атрибутом *Name* числом *20*.
Узнать атрибут Name у Input можно инспектором кода у браузера.

### 28) * Type the text into "Selector":
Печатает текст в инпуте.
```JavaScript 
* Type the text into "Input(entityCount)":
      """
      2
      """
```

Этот шаг универсальней предыдущего.. Он сам кликнет на нужный инпут и наберет в нем текст
___Предыдущий шаг тоже кликает на инпут. Разница в том, что этот шаг используется для ввода нескольких строк текста. Нужно переписать.___

### 29) * Type "Text"
Печатает текст. Предварительно нужно сфокусироваться на поле ввода.

### 30) * Set "Value" of the cell at the intersection of "CollName" and "RowName"
Выбирает определенный пункт в выпадающем списке ячейки на пересечении строки и колонки.
```
* Set "E-Property" of the cell at the intersection of "Enumerated List" and "Display Name Property"
```

### 31) * Type "Text" into the cell at the intersection of "CollName" and "RowName"
Печатает текст в ячейке на пересечении колонки и строки.
```
* Type "renamed" into the cell at the intersection of  "Code" and  "#5487"
```

### 32) * Type "Text" into the cell at the intersection of "CollName" and the row number [Number]
Печатает текст в ячейке на пересечении колонки с именем и строки с номером.

## Drag and Drop
### 33) * Drag "DndElement" and drop into "DndZone"
Перетаскивает DND элемент в указанную DND зону.
```
* Drag "Dnd Element(2.2 Клиенты)" and drop it into "Dnd Zone(Pages)"
```

### 33) * Drag "DndElement" and drop before "Element"
Захватывает левой клавишей мыши DND элемент, перетаскивает его и бросает перед указанным элементом.
```
* Drag "Dnd Zone(Available) > Dnd Element(Бренды)" and drop it before "Dnd Element(Filters)"
```

### 33) * Drag "DndElement" and drop after "DndZone"
Захватывает левой клавишей мыши DND элемент, перетаскивает его и бросает после указанного элемента.
```
* Drag "Dnd Zone(Available) > Dnd Element(Versions)" and drop it after "Dnd Element(Filters)"
```

### 34) * Drop file "File" to "Selector"
Прерносит файл из папки Fixtures в указанную область (импортирует файл).
```
* Drop file "Nomenklatura.xlsx" to "Grid"
```

### 35) Stop / Do not stop and show "red/green" text "Text" at position "Top/Middle/Bottom" for [Number] seconds
Показ титров.
```* "Stop" and show "red" text "Hello!!!" at the "Top" for [10] seconds```
Шаг выведет текст с нужным цветом расположенный в указанном месте на протяжении определенного времени


# Шаги связанные с кликом, наведением и выбором элемента

## Группа шагов
```
* Click on "Selector" - клик по селектору
* Right click on "Selector" - клип по селектору правой кнопкой мыши
* Double click on "Selector" - двойной клик по элементу
* Press and hold down the mouse button at "Selector" - нажать на селектор и не отпускать кнопку мыши (например для группового выделения в связке с шагом ниже)
* Release the mouse button at "Selector" - перетаскивание выделения до определенного селектора (например для группового выделения в связке с шагом выше)
* Hover over "Selector" - сфокуссироваться на элементе (наведение мыши)
```

## 36) * Click on "Selector" while holding "Key"
Шаг может кликнуть по чему-то с зажатой клавишей *SHIFT* или *Alt* и др.


## 37) * Click on text "Text" in "Selector"
Шаг предназначеный для клика по тексту в каком-то селекторе.
В данном примере произошел клик по фильтру с текстом Клин

** `*` Click on text "003" in "Tree Menu Element"** а в этом случае клик по тексту в открвшемся выпадающем списке фильтра.

** `*` Click on text "Apply & Save" in "Modal"** или когда есть недопустимые символы для других шагов, этот шаг сможет кликнуть на кнопку с названием Apply & Save в модальном окне


## 38) * Click on "Header Menu Element(1. Товарные группы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
Шаг открывает справочник который находится в иерархичном выпадающем меню. Для этого мы должны указать пункт меню Dimensions. В шаге произойдет фокусировка на этот элемент приложения. Почему именно на пункт меню сверху? Потому как Header Menu Element это прописанный селектор, название интерпритировано на человеческий язык, а внутри селектора лежит идентификтор по которому собественно и происходит вызов элемента.. В данном случае это класс **HeaderMenu__MenuItem**

```* Click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"```

Этот шаг работает по тому же принципу что и шаг выше, но в нём двойная вложенность.

```* Click on "Header Menu Element(Dimensions)"```

Шаг для клика по одному селектору с аргументом или если не указывать аргумент, то шаг нажмет на первый селектор в DOM дереве.

```* Click on "HeaderMenuElement" in "HeaderMenu" in "HeaderMenuElement" in "HeaderMenuElement"```


## 39) * Select element "Option" in "Selector"
Шаг выберет опцию в выпадающем списке указанного дропдауна
```* Select element "Start" in "Modal > Dropdown(position)"```


## 40) * Change the filter from "OldFilter" to "NewFilter"
Смена фильтра где мы указываем старый фильтр и тот на который переключим

---
# Нажатие клавиш клавиатуры

## 41) * Create a manual backup with a hotkey
Создание бекапа, в этом шаге заложено нажатие клавиш CTRL + S. Можно воспользоваться напрямую горячими клавишами если удобно


## 42) * Recalculate model with a hotkey
В шаге заложено нажа


## 43) * Press "Key"
```* Press "Enter"```

Шаг нажмет клавишу *Enter* или можно передавать другой аргумент в шаг. Список клавиш - https://github.com/puppeteer/puppeteer/blob/main/src/common/USKeyboardLayout.ts

```
* Press "Key" [Number] times
* Press "ARROW_DOWN" [5] times
```
Шаг нажимает клавишу *Down* 15 раз. Т.е. шаг может любое колличество раз нажать на нужную нам клавишу

```
* Press "Key" with "Key2"
* Press "PAGEDOWN" with "SHIFT"
```
Нажимает последовательно 2 клавиши клавиатуры

```
* Press "Key" with "Key2" [Number] times
* Press "ARROW_RIGHT" with "SHIFT" [9] times
```
Шаг зажмет клавишу *Shift* и будет нажимать клавишу *Right* 9 раз подряд

```* Press "E" with "SHIFT" with "CONTROL"```

Соответственно шаг нажмет клавишу *CTRL* c жажатым *Shift* и *E*

```
* Press "Key" with "Key2" and "Key3"
* Press "Key" with "Key2" and "Key3" [Number] times
```
Если понадобится, то можно нажать комбинацию и из трех клавиш несколько раз или один раз


---
# Шаги связанные со скролом

## 44) * Scroll the vertical scrollbar to the down
Вертикальный скролл грида проскролится в самый низ. Так-же можно проскролить этим шагом к началу или середине грида - *top* и *middle*
```
* Scroll the vertical scroller to the middle
* Scroll the vertical scroller to the top
```

## 45) * Scroll the horizontal scrollbar to the start
Горизонтальный скролл в гриде. Можно в начало, середину и конец страницы проскролить - *end* или *middle*
```
* Scroll the horizontal scrollbar to the middle
* Scroll the horizontal scrollbar to the end
```

## 46) * Scroll the "vertical" "Selector" by [Number] pixels
```* Scroll "vertical" "Modal > Dnd Zone(Free) > scroller" by "350" pixels```
Скролл вертикальный на 350px в модальном окне DND зоны с названием Free
```
* Scroll the "horizontal" "Selector" by [Number] pixels
* Scroll "horizontal" "Card of Dashboards(5.2 Вид РИМ) > scroller" by "300" pixels
```

Аналогично вертикальному можно сделать и горизонтальный скролл, правда в этом примере у карточки дашборда с определенным названием на 300px.
Сама карточка дашборда и скроллер должен попадать в зону видимости, иначе шаг не сможет проскролить.


## 47) * Check if the "vertical" scrollbar is scrolled by [Number] pixels
```* Check if the "horizontal" scrollbar is scrolled by [Number] pixels```

Шаги по проверке того, где находится скролл по горизонтали и вертикали в гриде.


## 48) * Check if the "vertical" "Selector" was scrolled by [Number] pixels
```
* Check if the "horizontal" "Card of Dashboards(big list) > scroller" was scrolled by "400" pixels
* Check if the "vertical" "Modal > Tree Menu > scroller" was scrolled by "104" pixels
```

В этих шагах проверяется конкректный скролл. 

## 49) * Scroll "Selector" to the "top/bottom/left/right" by [Number] pixels


## 50)    * Scroll the vertical scrollbar to the element "Selector"
Проскролить до нужной строки с названием

## 51)    * Scroll the kanban vertical scrollbar to the top
Вертикальный скролл в Kanban
```
* Scroll the kanban vertical scrollbar to the middle
* Scroll the kanban vertical scrollbar to the bottom
```

## 52)    * Scroll the kanban horizontal scrollbar to the start
Горизонтальный скролл в Kanban
```
* Scroll the kanban horizontal scrollbar to the middle
* Scroll the kanban horizontal scrollbar to the end
```

# Шаги с инсертом элементов

## 53) * Insert elements "Elements" at position "start/end/after/before":
```JavaScript 
* Insert elements "Elements" at position "start/end/after/before":
    """
    Test Half Subset 1
    Test Half Subset 2
    """
```

Шаг выполяющий несколько итераций. Кликает на кнопку Add (название кнопки, например Subsets) with Names - это множественный именованный инсерт.
Далее вводит название элементов в поле Textarea, выбирает позицию Start в выпадающем списке и нажимает кнопку Ok.
Если делать Named Insert справочника с позицией After, то шаг будет выглядеть так - *When I insert "Lists" elements at the "After":*


## 54) * Insert [Number] elements into "Element" at position "start/end/after/before/child of"
Шаг выполяющий несколько итераций. Кликает на кнопку Add (название кнопки, например Subsets) - Это множественный **не**именованный инсерт.
Далее вводит колличество элементов в input, выбирает позицию Start в выпадающем списке и нажимает кнопку Ok.


## 55) * Save the current view as "NewViewName"
Сохранение новой вьюхи МК. Для этого нужно находиться в нужном МК и шаг нажмет на кнопку View в Toolbar, выберет в выпадающем списке пункт Save As, в появившемся модальном окне запишет название новой вьюхи, все чекбоксы останутся дефолтными и кликнет на кнопку OK



[Список всех шагов](../steps/allSteps.md)

[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)
