
# Сервисные шаги

## 1)    * Start with an isolated model "ModelName"
Создание изолированной модели

## 2)    * Start with a not isolated model "ModelName"
Создание не изолированной модели

## 3)    * Start as a "User"
Открытие приложения из под определенного пользоваля. Используем для проверки функционала из под пользователей с разными правами - моделлеры, не моделлеры, лимитированные пользователи

## 4)    * Delete the current model
Удаление ранее созданной изолированной копии модели самим тестом. ***Нужно быть осторожным, если вы запустите тест в оригинальной модели, то шаг удалит вашу модель!***

## 5)    * Go to page "PageName"
Открыть страницу Drive Landing или Main

## 6)    * Open tab "ModuleName"
Откроет какой-либо элемент с указанным именем. Шаг выберет элемент из списка в поле Contents, перед этим произойдет перезагрузка страницы


## 3)    * Reload Page
Перезагрузка приложения



## 4) * Check if the Grid exists and loaded
Шаг проверят загрузку грида и отсуствие лоадера. Часто применяется после открытия нового грида или изменения состояния грида на котором находится пользователь. Когда заведомо известно, что грид должен загрузиться или обновиться, то применяем этот шаг. Можно не применять его если мы проверяем какие-то элементы в гриде. Например мы вошли в новый грид, проверили существование колонки с определенным названием или строки и это гарантирует нам что грид загружен, иначе элементов видно небыло-бы без загрузки грида.



## 1) * Check if "Selector" exists
> * Check if "Modal" **exists**

> * Check if "Row Header(Балтика)" exists

Есть шаги по проверке существования элементов - селекторов в приложении. Применяются они для того чтобы убедиться в том, появилось что либо после какого-нибудь события.

Альтернативные шаги следуют далее:

> * Сheck that "Selector" is checked
> * Сheck that "Selector" is not checked
* Сheck that "Grid Cell(7:0) > Checkbox" **is checked**

Можно проверять Boolean кнопку на ее состояние, **true**(***is checked***) или **false**(***is not checked***)
В этом примере у *Grid Cell(7:0)* есть Checkbox и мы проверяем его состояние.


> * Сheck that "Selector" is disabled
> * Сheck that "Selector" is not disabled
* Сheck that "Tab Header(Half Years)" **is disabled**

Проверка на свойство элемента, **disabled** или **is not disabled**
Вот еще пример: *And I see that "Modal > Button(Delete)" is disabled*


> * Сheck that "Selector" is active
> * Сheck that "Selector" is not active
* Сheck that "Modal > Tab Header(Basic)" **is active**

Првоерка на активность элемента. К напримеру у Табов в приложении есть такое состояние и мы можем проверять  активна ли она - **is active** или нет - **is not active**


> * Сheck that "Selector" is selected
* Сheck that "Modal > Tree Menu Element(test property for update)" is selected
Проверка на то, заселекчен ли элемент



## 2) * Check if "Selector" does not exist
* Check if "Row Header(Балтика)" does not exist
Шаг проверяет, что строки с таким-то именем **нет** в гриде.. Данный пример говорит о том, что шагом мы проверяем элемент который отсуствет после применения функционала Hide или другого скрытия(удаления к примеру).

Важно перед таким шагом проверять существование других элементов или завершение загрузки грида
```
* Check if the Grid exists and loaded
* Check if "Row Header(1:-1)" does not exist
```

 или 

 ```
And I click on "Menu Item(Hide) > Menu Item(All Entries)"
* Check if the Grid exists and loaded
* Check if "Row Header(Толстяк)" exists
* Check if "Row Header(Балтика)" does not exist
```



## 5) * Check if the text in "Selector" equals to "Text"
* Check if the text in "-1,234.56789" equals to "Modal > Sample Value"
Шаг для проверки текста у определенного селектора или у контейнера.
Представим что у нас есть модальное окно и нам нужно проверить часть текста `-1,234.56789` в этом нам и поможет этот шаг.


## 6) * Check if "Selector" does not contain "Text"
Шаг проверит отсуствие текста у указанного селектора


## 6) * Check if "Selector" attribute value "value" equals to "Value"
* Check that "Modal > Input(dependOn)" attribute value value equals to "1.2 Контрагенты"
Проверка значения в инпуте


## 9) * Check if "Selector" property value equals to "Value"
* Check if "Grid Cell Editor" property value equals to "VCAR_01_01"
Проверка свойства property у определенного элемента



## 10) * Check if the property value for "CollName" and "RowName" equals to "Value"
 * Check if the property value for "О1.2" and "Text col with data" equals to "444"
Проверка property на пересечении Строки и Колонки.
- Первый аргумент О1.2 - это название колонки
- Text col with data - название строки. 
- 444 - данные в ячейке



## 11) * Check elements in the grid:
```JavaScript 
* Check elements in the grid:
    | 0:-1 | cube 1 | 21   | 17 |
    | 1:-1 | cube 2 | О1.2 | В2 |
```

Шаг проверяет данные в гриде, с указанием номера строки и данных в колонках. Колонки отбиваются друг от друга символом **|** 

Есть возможность не указывать значения клеток **|  |** оставить контейнер пустым



## 11) * Check if the elements in context ""DashboardSelector"" grid match:
  | 0:-1 | Value | Value | Value |
  | 1:-1 | Value | Value | Value |"


## 1)    * Check if element "Selector" is visible now
* Check if element "Card of Dashboards(1.1 Страны) > Loader" is visible now
Отстуствие элемента на странице в данный момент вермени!


## 7) * Check if value "Value" was inputted in "Selector"
Проверяет value у инпута с названием


## 41) * Check if "Selector" is shown
Проверка существования элемента и то что он видим


## 42) * Check if "Selector" is not shown
Проверка того, что элемента не видно


## 11)    * Check if "Selector" with text "Text" is active
Используется для роверки на то, активен ли таб

## 12)    * Check if "Selector" with text "Text" is not active
* Check if "Tab Header" with text "Half Years" is not active
Проверка на то, не активен ли таб




## 9)    * Wait until the modal form is open
Ожидание открытия модального окна


## 10)   * Clear "Selector"
* Clear "Conditional Formatting(Maximum) > Input"
Очистка значения в поле input. В качестве аргумента указывается атрибут Name нужного input



## 22) * Set value "Value" to "Selector"
* Set value "Big multicube" to "Module Name"
Шаг введет текст *Big multicube* в инпут у которого атрибут *Name* = Module Name


## 20) * Type "Text" into "Selector"
* Type "20" into "Input(fontSize)"
Шаг введет данные в поле ввода(Input) с атрибутом *Name* числом *20*.
Узнать атрибут Name у Input можно инспектором кода у браузера.


## 21) * Type the text into "Selector":
```JavaScript 
* Type the text into "Input(entityCount)":
      """
      2
      """
```

Этот шаг универсальней предыдущего.. Он сам кликнет на нужный инпут и наберет в нем текст


## 25) * Type "Text"
Шаг наберет указанный текст. Правда перед этим шагом нужно выбрать место где наберется этот текст.


## 26) * Set "Value" of the cell at the intersection of "CollName" and "RowName"
* Set "E-Property" of the cell at the intersection of "Enumerated List" and "Display Name Property"
Выбор определенного пункта в выпадающем списке на пересечении строки и колонки.

## 26) * Type "Text" into the cell at the intersection of "CollName" and "RowName"
* Type "renamed" into the cell at the intersection of  "Code" and  "#5487"
Шаг прописывает текст на пересечении колонки и строки

## 26) * Type "Text" into the cell at the intersection of "CollName" and the row number [Number]
Шаг прописывает текст на пересечении колонки и номером строки



## 38) * Drag "DndElement" and drop into "DndZone"
С помощью этого шага возможно перетаскивать определенные DND элементы на другие зоны или элементы

> * Drag "DndElement" and drop before "DndElement"

Можно перенести над каким-то элементом

> * Drag "DndElement" and drop after "DndElement"

Можно перенести под какой-то элемент



## 35) * Drop file "File" to "Selector"
When I drop file "Nomenklatura.xlsx" to the "Grid"

Шаги для переноса файлов из папки Fixtures в наш грид или еще какую-то область. Это позволяет сделать импорт подготовленного файла



## 33) Stop / Do not stop and show "red/green" text "Text" at position "Top/Middle/Bottom" for [Number] seconds
* "Stop" and show "red" text "Hello!!!" at the "Top" for [10] seconds
Шаг выведет текст с нужным цветом расположенный в указанном месте на протяжении определенного времени



# Шаги связанные с кликом, наведением и выбором элемента

## Группа шагов
* Click on "Selector" - клик по селектору
* Right click on "Selector" - клип по селектору правой кнопкой мыши
* Double click on "Selector" - двойной клик по элементу
* Press and hold down the mouse button at "Selector" - нажать на селектор и не отпускать кнопку мыши (например для группового выделения в связке с шагом ниже)
* Release the mouse button at "Selector" - перетаскивание выделения до определенного селектора (например для группового выделения в связке с шагом выше)
* Hover over "Selector" - сфокуссироваться на элементе (наведение мыши)


## 15) * Click on "Selector" while holding "Key"
Шаг может кликнуть по чему-то с зажатой клавишей *SHIFT* или *Alt* и др.


## 14) * Click on text "Text" in "Selector"
Шаг предназначеный для клика по тексту в каком-то селекторе.
В данном примере произошел клик по фильтру с текстом Клин

**(`*`) Click on text "003" in "Tree Menu Element"** а в этом случае клик по тексту в открвшемся выпадающем списке фильтра.

**(`*`) Click on text "Apply & Save" in "Modal"** или когда есть недопустимые символы для других шагов, этот шаг сможет кликнуть на кнопку с названием Apply & Save в модальном окне



## 13) * Click on "Header Menu Element(1. Товарные группы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"

Шаг открывает справочник который находится в иерархичном выпадающем меню. Для этого мы должны указать пункт меню Dimensions. В шаге произойдет фокусировка на этот элемент приложения. Почему именно на пункт меню сверху? Потому как Header Menu Element это прописанный селектор, название интерпритировано на человеческий язык, а внутри селектора лежит идентификтор по которому собественно и происходит вызов элемента.. В данном случае это класс **HeaderMenu__MenuItem**

> * Click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"

Этот шаг работает по тому же принципу что и шаг выше, но в нём двойная вложенность.

> * Click on "Header Menu Element(Dimensions)"

Шаг для клика по одному селектору с аргументом или если не указывать аргумент, то шаг нажмет на первый селектор в DOM дереве.

> * Click on "HeaderMenuElement" in "HeaderMenu" in "HeaderMenuElement" in "HeaderMenuElement"



## 17) * Select element "Option" in "Selector"
Шаг выберет опцию в выпадающем списке указанного дропдауна
* Select element "Start" in "Modal > Dropdown(position)"


## 19) * Change the filter from "OldFilter" to "NewFilter"
Смена фильтра где мы указываем старый фильтр и тот на который переключим



# Нажатие клавиш клавиатуры

## 36) * Create a manual backup with a hotkey
Создание бекапа, в этом шаге заложено нажатие клавиш CTRL + S. Можно воспользоваться напрямую горячими клавишами если удобно


## 37) * Recalculate model with a hotkey
В шаге заложено нажа



## 32) * Press "Key"
> * Press "Enter"

Шаг нажмет клавишу *Enter* или можно передавать другой аргумент в шаг. Список клавиш - https://github.com/puppeteer/puppeteer/blob/main/src/common/USKeyboardLayout.ts


> * Press "Key" [Number] times
* Press "ARROW_DOWN" [5] times
Шаг нажимает клавишу *Down* 15 раз. Т.е. шаг может любое колличество раз нажать на нужную нам клавишу

> * Press "Key" with "Key2"
* Press "PAGEDOWN" with "SHIFT"
Нажимает последовательно 2 клавиши клавиатуры

> * Press "Key" with "Key2" [Number] times
* Press "ARROW_RIGHT" with "SHIFT" [9] times
Шаг зажмет клавишу *Shift* и будет нажимать клавишу *Right* 9 раз подряд

> * Press "E" with "SHIFT" with "CONTROL"

Соответственно шаг нажмет клавишу *CTRL* c жажатым *Shift* и *E*

> * Press "Key" with "Key2" and "Key3"
> * Press "Key" with "Key2" and "Key3" [Number] times
Если понадобится, то можно нажать комбинацию и из трех клавиш несколько раз или один раз



---
# Шаги связанные со скролом

## 41) * Scroll the vertical scrollbar to the down
Вертикальный скролл грида проскролится в самый низ. Так-же можно проскролить этим шагом к началу или середине грида - *top* и *middle*
* Scroll the vertical scroller to the middle
* Scroll the vertical scroller to the top

## 42) * Scroll the horizontal scrollbar to the start
Горизонтальный скролл в гриде. Можно в начало, середину и конец страницы проскролить - *end* или *middle*
* Scroll the horizontal scrollbar to the middle
* Scroll the horizontal scrollbar to the end

## 43) * Scroll the "vertical" "Selector" by [Number] pixels
* Scroll "vertical" "Modal > Dnd Zone(Free) > scroller" by "350" pixels
Скролл вертикальный на 350px в модальном окне DND зоны с названием Free

* Scroll the "horizontal" "Selector" by [Number] pixels
> Scroll "horizontal" "Card of Dashboards(5.2 Вид РИМ) > scroller" by "300" pixels

Аналогично вертикальному можно сделать и горизонтальный скролл, правда в этом примере у карточки дашборда с определенным названием на 300px.
Сама карточка дашборда и скроллер должен попадать в зону видимости, иначе шаг не сможет проскролить.


## 44) * Check if the "vertical" scrollbar is scrolled by [Number] pixels
* Check if the "horizontal" scrollbar is scrolled by [Number] pixels

Шаги по проверке того, где находится скролл по горизонтали и вертикали в гриде.


## 45) * Check if the "vertical" "Selector" was scrolled by [Number] pixels
* Check if the "horizontal" "Card of Dashboards(big list) > scroller" was scrolled by "400" pixels
* Check if the "vertical" "Modal > Tree Menu > scroller" was scrolled by "104" pixels

В этих шагах проверяется конкректный скролл. 

## 45) * Scroll "Selector" to the "top/bottom/left/right" by [Number] pixels


## 13)    And I scroll vertical scroller to element ""
Проскролить до нужной строки с названием

## 14)    * Scroll the kanban vertical scrollbar to the top
Вертикальный скролл в Kanban
* Scroll the kanban vertical scrollbar to the middle
* Scroll the kanban vertical scrollbar to the bottom

## 15)    * Scroll the kanban horizontal scrollbar to the start
Горизонтальный скролл в Kanban
* Scroll the kanban horizontal scrollbar to the middle
* Scroll the kanban horizontal scrollbar to the end



# Шаги с инсертом элементов

## 28) * Insert elements "Elements" at position "start/end/after/before":
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


## 29) * Insert [Number] elements into "Element" at position "start/end/after/before/child of"
Шаг выполяющий несколько итераций. Кликает на кнопку Add (название кнопки, например Subsets) - Это множественный **не**именованный инсерт.
Далее вводит колличество элементов в input, выбирает позицию Start в выпадающем списке и нажимает кнопку Ok.


## 34) * Save the current view as "NewViewName"
Сохранение новой вьюхи МК. Для этого нужно находиться в нужном МК и шаг нажмет на кнопку View в Toolbar, выберет в выпадающем списке пункт Save As, в появившемся модальном окне запишет название новой вьюхи, все чекбоксы останутся дефолтными и кликнет на кнопку OK




[Список всех шагов](../steps/allSteps.md)

[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)