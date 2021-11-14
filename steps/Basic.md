
# Basic-шаги (Часто используемые)

## 1. Сервисные шаги

### 1.1. * Start with an isolated model "ModelName"
Создает копию модели (изолированную модель) и запускает ее.

### 1.2. * Start with a not isolated model "ModelName"
Запускает оригинальную (не изолированную) модель.

### 1.3. * Start as a "User"
Запускает приложение с правами доступа определенного пользоваля, например: Modeller, Developer, Not Modeller.

### 1.4. * Delete the current model
Удаляет ранее созданную копию модели (изолированную модель).

***Нужно быть осторожным, если вы запустите тест в оригинальной модели, то шаг удалит вашу модель!***

### 1.5. * Go to page Drive Landing
Открывает страницу Drive Landing.

### 1.6. * Go to page Contents Page
Открывает страницу Contents Page.

### 1.7. * Open tab "ModuleName"
Переходит на страницу Contents и открывает вкладку с указанным именем.

### 1.8. * Reload Page
Перезагружает страницу.

### 1.9. * Wait until the modal form is open
Ожидает открытие модального окна.

## 2. Проверка существования элементов

### 2.1. * Check if the Grid exists and loaded
Шаг проверят загрузку грида и отсуствие лоадера. Часто применяется после открытия нового грида или изменения состояния грида на котором находится пользователь. Когда заведомо известно, что грид должен загрузиться или обновиться, то применяем этот шаг. Можно не применять его если мы проверяем какие-то элементы в гриде. Например мы вошли в новый грид, проверили существование колонки с определенным названием или строки и это гарантирует нам что грид загружен, иначе элементов видно небыло-бы без загрузки грида.

### 2.2. * Check if "Selector" exists
Проверяет существование элемента на странице.
```
* Check if "Modal" exists
* Check if "Row Header(Балтика)" exists
* Check if "Any Loader" exists
```

### 2.3. * Check if "Selector" does not exist
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

### 2.4. * Check if "Selector" contains "Text"
Проверяет что элемент содержит текст.
```
* Check if "Modal > Sample Value" contains "-1,234.56789"
```
Проверяет что в модальном окне есть текст `-1,234.56789`.

### 2.5. * Check if "Selector" does not contain "Text"
Проверяет что элемент не содержит текст.

### 2.6. * Check if "Selector" attribute value equals to "Value"
Проверяет значение в инпуте.
```
* Check if "Modal > Input(dependOn)" attribute value equals to "1.2 Контрагенты"
```

### 2.7. * Check if "Selector" property value equals to "Value"
Проверяет свойство property у определенного элемента.
```
* Check if "Grid Cell Editor" property value equals to "VCAR_01_01"
```

### 2.8. * Check if the property value for "CollName" and "RowName" equals to "Value"
Проверяет значение в ячейке на пересечении строки и колонки с именами.
```
* Check if the property value for "О1.2" and "Text col with data" equals to "444"
```
- Первый аргумент О1.2 - название колонки
- Text col with data - название строки. 
- 444 - данные в ячейке

### 2.9. * Check if the elements in the grid match:
Проверяет что грид содержит значения.
```JavaScript 
* Check if the elements in the grid match:
    | 0:-1 | cube 1 | 21 | 17 |
    | 1:-1 | cube 2 |  2 | В2 |
```
Шаг проверяет данные в гриде, с указанием номера строки и данных в колонках. Колонки отбиваются друг от друга символом **|** 

Есть возможность не указывать значения клеток **|  |** оставить контейнер пустым

### 2.10. * Check if the elements in the grid do not match:
Проверяет что грид не содержит значения.
```JavaScript 
* Check if the elements in the grid do not match:
    | 0:-1 | cube 1 | 21 | 17 |
    | 1:-1 | cube 2 |  2 | В2 |
```

### 2.11. * Check if the elements in context "DashboardSelector" grid match:
Проверяет что грид в карточке дашборда содержит значения.
```JavaScript 
* Check if the elements in context "Card of Dashboards(Data Input Check)" grid match:
  | 0:-1 | Value | Value | Value |
  | 1:-1 | Value | Value | Value |
```
### 2.12. * Check if the elements in context "DashboardSelector" grid do not match:
Проверяет что грид в карточке дашборда не содержит значения.
```JavaScript 
* Check if the elements in context "Card of Dashboards(Data Input Check)" grid do not match:
  | 0:-1 | Value | Value | Value |
  | 1:-1 | Value | Value | Value |
```

### 2.13. * Сheck if the input value in "Selector" equals to "Value"
Проверяет что введенный в поле ввода текст равен значению.
```
* Check if the input value in "Search Input" equals to "189942"
```

### 2.14. * Check if "Selector" with text "Text" is active
Проверяет что вкладка с названием “Text” активна.
```
* Check if "Tab Header" with text "Half Years" is active
```

### 2.15. * Check if "Selector" with text "Text" is not active
Проверяет что вкладка с названием “Text” не активна.
```
* Check if "Tab Header" with text "Half Years" is not active
```

## 3. Работа с Инпутами

### 3.1. * Clear value in "Selector"
Очищает значения в поле input. В качестве аргумента указывается атрибут Name нужного input.
```
* Clear value in "Input(search)"
```

### 3.2. * Type "Text" into "Selector"
Печатает текст в инпуте.
```
* Type "20" into "Input(fontSize)"
```
Шаг введет текст - *20* в *Input* у которого атрибут name - *fontSize*.
Узнать атрибут Name у Input можно инспектором кода у браузера.

### 3.3. * Type the text into "Selector":
Печатает текст в инпуте.
```JavaScript 
* Type the text into "Input(entityCount)":
      """
      2
      """
```

Этот шаг универсальней предыдущего.. Он сам кликнет на нужный инпут и наберет в нем текст. Разница в том, что этот шаг используется для ввода нескольких строк текста.

### 3.4. * Type "Text"
Печатает текст. Предварительно нужно сфокусироваться на поле ввода.

### 3.5. * Set "Value" of the cell at the intersection of "CollName" and "RowName"
Выбирает определенный пункт в выпадающем списке ячейки на пересечении строки и колонки.
```
* Set "E-Property" of the cell at the intersection of "Enumerated List" and "Display Name Property"
```

### 3.6. * Type "Text" into the cell at the intersection of "CollName" and "RowName"
Печатает текст в ячейке на пересечении колонки и строки.
```
* Type "renamed" into the cell at the intersection of  "Code" and  "#5487"
```

### 3.7. * Type "Text" into the cell at the intersection of "CollName" and the row number [Number]
Печатает текст в ячейке на пересечении колонки с именем и строки с номером.

## 4. Drag and Drop
### 4.1. * Drag "DndElement" and drop into "DndZone"
Перетаскивает DND элемент в указанную DND зону.
```
* Drag "Dnd Element(2.2 Клиенты)" and drop it into "Dnd Zone(Pages)"
```

### 4.2. * Drag "DndElement" and drop before "Element"
Захватывает левой клавишей мыши DND элемент, перетаскивает его и бросает перед указанным элементом.
```
* Drag "Dnd Zone(Available) > Dnd Element(Бренды)" and drop it before "Dnd Element(Filters)"
```

### 4.3. * Drag "DndElement" and drop after "DndZone"
Захватывает левой клавишей мыши DND элемент, перетаскивает его и бросает после указанного элемента.
```
* Drag "Dnd Zone(Available) > Dnd Element(Versions)" and drop it after "Dnd Element(Filters)"
```

### 4.4. * Drop file "File" to "Selector"
Прерносит файл из папки Fixtures в указанную область (импортирует файл).
```
* Drop file "Nomenklatura.xlsx" to "Grid"
```

### 4.5. Stop / Do not stop and show "red/green" text "Text" at position "Top/Middle/Bottom" for [Number] seconds
Показ титров.
```* "Stop" and show "red" text "Hello!!!" at the "Top" for [10] seconds```
Шаг выведет текст с нужным цветом расположенный в указанном месте на протяжении определенного времени


## 5. Действия с Элементами

### 5.1. * Click on "Selector"
Делает клик левой клавишей мыши по элементу
```
* Click on "Tab Header(Settings)"
```

### 5.2. * Right click on "Selector"
Делает клик правой клавишей мыши по элементу
```
* Right click on "Grid Cell(2:1)"
```

### 5.3. * Double click on "Selector"
Делает двойной клик левой клавишей мыши по элементу
```
* Double click on "Card Of Dashboards(Editable Module) > Grid Cell(0:4)"
```

### 5.4. * Hover over "Selector"
Наводит курсор мыши на элемент
```
* Hover over "Card Of Dashboards(Multicubes – Cubes) > SwitchToolbar"
```

### 5.5. * Click on "Selector" while holding "Key"
Делает клик левой клавишей мыши по элементу с зажатой клавишей клавиатуры
```
* Click on "Row Header(4:-2, Line Item 3)" while holding "CONTROL"
```

### 5.6. * Right click on "Selector" while holding "Key"
Делает клик правой клавишей мыши по элементу с зажатой клавишей клавиатуры
```
* Right click on "Grid Cell(37:13)" while holding "SHIFT"
```

### 5.7. * Click on text "Text" in "Selector"
Делает клик левой клавишей мыши по тексту в элементе
```
* Click on text "4500" in "Search Results"
* Click on text "#221" in "Tree Menu Element"
клик по тексту в открывшемся выпадающем списке фильтра
* Click on text "Apply & Save" in "Modal"
клик по кнопке с названием Apply & Save в модальном окне
```

### 5.8. * Click on "HeaderMenuElement" in "HeaderMenu"
Делает клик левой клавишей мыши по элементу, расположенному в Header Menu первого уровня.
```
* Click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"
```

### 5.9. * Click on "HeaderMenuElement" in "HeaderMenu" in "HeaderMenuElement"
Делает клик левой клавишей мыши по элементу, расположенному в Header Menu второго уровня.
```
* Click on "Header Menu Element(1.1 Countries)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
```

### 5.10. * Click on "HeaderMenuElement" in "HeaderMenu" in "HeaderMenuElement" in "HeaderMenuElement"
Делает клик левой клавишей мыши по элементу, расположенному в Header Menu третьего уровня.
```
* Click on "Header Menu Element(Add Subset in Quarters)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Time)" in "Header Menu Element(Quarters)"
```

### 5.11. * Select element "Option" in "Selector"
Выбирает опцию в выпадающем списке указанного дропдауна. У дропадуна есть атрибут name который мы можем указать - *Dropdown(position)*
```
* Select element "Start" in "Modal > Dropdown(position)"
* Select element "UTF-8" in "Dropdown(encoding)"
```

### 5.12. * Change the filter from "OldFilter" to "NewFilter"
Меняет фильтр с OldFilter на NewFilter.
```
* Change the filter from "Budget" to "Actual"
```

# 6. Нажатие клавиш клавиатуры

### 6.1. * Open the context menu with a hotkey
Открывает диалоговое окно (комбинация клавиш CTRL + Q).

### 6.2. * Create a manual backup with a hotkey
Создание бекапа модели (комбинация клавиш CTRL + S).

### 6.3. * Recalculate model with a hotkey
Включает пересчет модели (нажимает клавишу F9)

### 6.4. * Press "Key"
Нажимает клавишу клавиатуры один раз.
```
* Press "Enter"
* Press "ARROW_DOWN"
```

### 6.5. * Press "Key" [Number] times
Нажимает клавишу клавиатуры несколько раз.
```
* Press "ARROW_DOWN" [5] times
```

### 6.6. * Press "Key" with "Key2"
Нажимает клавишу клавиатуры с зажатой клавишой Key2.
```
* Press "ARROW_RIGHT" with "SHIFT"
* Press "PAGEDOWN" with "SHIFT"
```

### 6.7. * Press "Key" with "Key2" [Number] times
Нажимает клавишу клавиатуры с зажатой клавишой Key2 несколько раз.
```
* Press "ARROW_RIGHT" with "SHIFT" [9] times
* Press "PAGEDOWN" with "SHIFT" [3] times
```

### 6.8. * Press "Key" with "Key2" and "Key3"
Нажимает клавишу клавиатуры с зажатыми клавишами Key2 и Key3.
```
* Press "L" with "SHIFT" and "ALT"
* Press "E" with "SHIFT" and "CONTROL"
```
Список клавиш - https://github.com/puppeteer/puppeteer/blob/main/src/common/USKeyboardLayout.ts

---
## 7. Шаги связанные со скролом

### 7.1. * Scroll the vertical scrollbar to the top
Скроллит грид вертикально вверх.

### 7.2. * Scroll the vertical scrollbar to the middle
Скроллит грид вертикально вцентр.

### 7.3. * Scroll the vertical scrollbar to the bottom
Скроллит грид вертикально вниз.

### 7.4. * Scroll the horizontal scrollbar to the start
Скролит грид горизонтально в начало.

### 7.5. * Scroll the horizontal scrollbar to the middle
Скролит грид горизонтально в центр.

### 7.6. * Scroll the horizontal scrollbar to the end
Скролит грид горизонтально в конец.

### 7.7. * Scroll the kanban vertical scrollbar to the top
Скроллит канбан вертикально вверх.

### 7.8. * Scroll the kanban vertical scrollbar to the middle
Скроллит канбан вертикально вцентр.

### 7.9. * Scroll the kanban vertical scrollbar to the bottom
Скроллит канбан вертикально вниз.

### 7.10. * Scroll the kanban horizontal scrollbar to the start
Скроллит канбан горизонтально в начало.

### 7.11. * Scroll the kanban horizontal scrollbar to the middle
Скроллит канбан горизонтально в центр.

### 7.12. * Scroll the kanban horizontal scrollbar to the end
Скроллит канбан горизонтально в конец.

### 7.13. * Scroll the "vertical" "Selector" by [Number] pixels
Скроллит элемент вертикально на определенное количество пикселей.
```
* Scroll the "vertical" "Modal > Dnd Zone(Available) > scroller" by [500] pixels
```

### 7.14. * Scroll the "horizontal" "Selector" by [Number] pixels
Скроллит элемент горизонтально на определенное количество пикселей.
```
* Scroll the "horizontal" "Card of Dashboards(big list) > scroller" by [400] pixels
```

### 7.15. * Scroll "Selector" to the "top/bottom/left/right" by [Number] pixels
Скролит элемент вверх, вниз, влево или вправо на определенное количество пикселей.
```
* Scroll "Modal > Chart Scroll Conteiner" to the "down" by [350] pixels
* Scroll "Modal > Chart Scroll Conteiner" to the "top" by [350] pixels
* Scroll "Modal > Chart Scroll Conteiner" to the "left" by [350] pixels
* Scroll "Modal > Chart Scroll Conteiner" to the "right" by [350] pixels
```

### 7.16. * Check if the "vertical/horizontal" scrollbar is scrolled by [Number] pixels
Проверяет что грид проскролен вертикально или горизонтально на определенное количество пикселей.
```
* Check if the "vertical" scrollbar is scrolled by [300] pixels
* Check if the "horizontal" scrollbar is scrolled by [500] pixels
```

### 7.17. * Check if the "vertical/horizontal" "Selector" was scrolled by [Number] pixels
Проверяет что элемент проскролен вертикально или горизонтально на определенное количество пикселей
```
* Check if the "vertical" "Modal > Tree Menu > scroller" was scrolled by [1300] pixels
* Check if the "horizontal" "Card of Dashboards(big list) > scroller" was scrolled by [250] pixels
```

## 8. Вставка элементов

### 8.1. * Insert elements "Elements" at position "start/end/after/before":
Добавление именованных элементов.
```JavaScript 
* Insert elements "Lists" at position "start":
  “““
   List 3
   List 1
  “““
```
Шаг выполняет несколько итераций: кликает на кнопку "Add (название кнопки, например Subsets) with Names" - это множественный именованный инсерт, вводит название элементов в поле Textarea, выбирает позицию в выпадающем списке и нажимает кнопку Ok.

### 8.2. * Insert [Number] elements into "Element" at position "start/end/after/before/child of"
Добавление неименованных элементов.
```
* Insert [5] elements into "Lists" at position "after"
```
Шаг выполняет несколько итераций: кликает на кнопку "Add (название кнопки, например Subsets)" - это множественный **не**именованный инсерт, вводит колличество элементов в input, выбирает позицию в выпадающем списке и нажимает кнопку Ok.

### 8.3. * Save the current view as "NewViewName"
Сохраняет новую вьюху.
```
* Save the current view as "Test View Tab"
```
Шаг выполняет несколько итераций: нажимает на кнопку View в Toolbar, выбирает в выпадающем списке пункт Save As, вводит название новой вьюхи и нажимает на кнопку OK. Применимо для грида в которых можно сохранять вьюхи.

[Список всех шагов](../steps/allSteps.md)

[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)
