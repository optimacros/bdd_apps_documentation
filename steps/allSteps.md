# Список всех шагов

## Комлпексные шаги:

1) > When I click on "Header Menu Element(1. Товарные группы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"

Шаг открывает справочник который находится в иерархии меню. Для этого мы должны указать пункт меню Dimensions. В шаге произойдет фокусировка на этот элемент приложения. Почему именно на пункт меню сверху? Потому как Header Menu Element это прописанный селектор, название интерпритировано на человеческий язык, а внутри селектора лежит идентификтор по которому собественно и происходит вызов элемента.. В данном случае это класс ```HeaderMenu__MenuItem```

 > When I click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"
Этот шаг работает по тому же принципу что и шаг выше. Но сдесь двойная вложенность

 > When I click on "Header Menu Element(Dimensions)" 
Шаг для клика по одному селектору с аргументом или если не указывать аргумент, то шаг нажмет на первый селектор в DOM дереве

2) > When I hover on "Header Menu Element(Dimensions)"
Шаг наводящий курсор мыши на указанный элемент

3) > When I type "20" into "Input(fontSize)"
Шаг напечатает в поле ввода с атрибутом *Name* число *20*
Узнать атрибут Name у Input можно инспектором кода у браузера

4) > When I click by coordinates "275:390"
 > When I hover by coordinates "275:390"
Шаг наведет курсор или кликнет по координатам приложения, если по этой координате будет какой-то элемент, то произойдет какое-то событие. Чаще всего этот шаг применяется для клика по нужному элементу в графике. Дело в том что в графиках тяжело привязаться к элементу и сделать с ним что-то. Ну а к самим настройкам графика мы можем обратиться, многие селекторы уже прописаны. 

5) ```When I type "Test"```
Шаг наберет указанный текст. Правда перед этим шагом нужно выбрать место где набередтся этот текст. Мы можем например кликнуть этим шагом *And I click on "Input(newItems)"*

6) ``` And I type into "Input(entityCount)":```
      """
      2
      """

Этот шаг универсальней предыдущего.. Он сам кликнет на нужный инпут и наберет в нем текст

8) - ```And I press "ENTER"``` 
Шаг нажимает клавишу *Enter* или можно передавать другой аргумент в шаг. Список клавиш - 

- ```And I press "ARROW_DOWN" [15] times```
Шаг нажимает клавишу *Down* 15 раз. Т.е. шаг может любое колличество раз нажать на нужную нам клавишу

- ```And I press "ARROW_LEFT" with "SHIFT" [9] times```
Шаг нажмет клавишу *Shift* вместе с *Left* 9 раз подряд

- ```When I press "E" with "SHIFT" with "CONTROL"```
Соответственно шаг нажмет клавишу *CTRL* c жажатым *Shift* и *E*

- ```When I press "E" with "SHIFT" with "CONTROL" [2] times```
Если понадобится, то можно нажать комбинацию и из трех клавиш несколько раз


9) - ```And I see that "Modal" exists``` 
```And I see that "Row Header(Балтика)" exists```
```And I see "Grid Cell Editor"```
Есть шаги по проверке существования элементов - селекторов в приложении.. Применяются они для того чтобы убедиться в том, появилось что либо после како-нибудь события.
Альтернативный шаг в следущем пункте

- ```When I see that "Grid Cell(7:0) > Checkbox" is checked```
Можно проверять Boolean кнопку на ее состояние, true(is checked) или false(is not checked)
В этом примере у Grid Cell(7:0) есть Checkbox и мы проверяем его состояние

- ```And I see that "Tab Header(Half Years)" is disabled```
Проверка на свойство элемента, disabled или is not disabled
Вот еще пример *And I see that "Modal > Button(Delete)" is disabled*

- ```And I see that "Modal > Tab Header(Basic)" is active```
Првоерка на активность элемента.. например у Табов в приложении есть такое состояние и мы можем проверять таба активна - is active или нет - is not active

- ```And I see that "Formula Input" is focused```
Самый редко используемый шаг на проверку фокуса на элементе.

10) ```And I see that "Row Header(Балтика)" doesn't exist```
Шаг проверяет что строки с таким то именем нет в гриде.. Данный пример говорит о том, что шаг мы проверяем элемент что он отсуствет после применения функционала Hide или другого скрытия.
Важно перед таким шагом проверять существование других элементов или завершение загрузки грида
```
And I see that Grid exists and loaded
And I see that "Row Header(1:-1)" doesn't exist
```
 или 
 ```
And I click on "Menu Item(Hide) > Menu Item(All Entries)"
And I see that Grid exists and loaded
And I see that "Row Header(Толстяк)" exists
Then I see that "Row Header(Балтика)" doesn't exist
```

```Then I don't see "Grid Cell Editor"```
Так же есть похожий шаг по проверке остуствия селектора, отличий с *doesn't exist* нет


11) ```And I see that "Card Of Dashboards(Cube МК4 Стандартные заказы и Номенклатура 4) > Grid Cell(2:1, 99)" exists for a long time```
Специфичный шаг, нужный для проверки сущесовования элемента но с увеличенным таймаутом самого шага.. В стандартных шагах заложен таймаут в 60 секунд, по истечению этого времени шаг упадет. Т.е. не дождется элемента и сценарий остановится и продолжится другой сценарий который вероятно тоже упадет так как в предыдущем сценарии не выполнились все заложенные действия

12) ```And I see that Grid exists and loaded```
Шаг проверят загрузку грида и отсуствие лоадера. Часто применяется после открытия нового грида или изменения состояния грида на котором находимся.. Когда мы заведомо знаем что грид должен загрузиться, то применяем этот шаг. Можно не применять его если мы проверяем какие-то элементы в гриде. Например мы вошли в новый грид, проверили существование колонки с определенным названием или строки и это гарантирует нам что грид загружен, иначе элементов видно небыло бы без загрузки грида.

13) ```And I see that Grid exists and loaded in [15] seconds```
Шаг выполняет провергу загрузки грида в течении 15 секунд. Если за 15 секунд грид не загрузился, то шаг упадет. Выставить мы можем время в пределах 60 секунд

14) ```Then I see text "-1,234.56789" in "Modal > Sample Value"```
Шаг для проверки текста у определенного селектора или у контейнера.
Представим что у нас есть модальное окно и нам нужно проверить часть текста `-1,234.56789` в этом нам и поможет наш шаг

15) ```And I don't see "Chart" with text "308.2K"```
Шаг проверит отсуствие текста у селектора


16) ```When I click on text "Клин" in "Filters"```
Шаг предназначеный для клика по тексту в каком-то селекторе.
В данном примере произошел клик по фильтру с текстом Клин
*And I click on text "003" in "Tree Menu Element"* а в этом случае клик по тексту в открвшемся выпадающем списке фильтра.
*And I click on text "Apply & Save" in "Modal"* или когда есть недопустимые символы для других шагов, этот шаг сможет кликнуть на кнопку с названием Apply & Save в модальном окне

17) 
```When I insert "Subsets" elements at the "Start":
      """
      Test Half Subset 1
      Test Half Subset 2
      """```

Шаг выполяющий несколько итераций. Кликает на кнопку Add (название кнопки, например Subsets) with Names - это множественный именованный инсерт.
Далее вводит название элементов в поле Textarea, выбирает позицию Start в выпадающем списке и нажимает кнопку Ok.
Если делать Named Insert справочника с позицией After, то шаг будет выглядеть так - *When I insert "Lists" elements at the "After":*

18) ```And I insert "2" elements type of "Elements" at the "Start"```
Шаг выполяющий несколько итераций. Кликает на кнопку Add (название кнопки, например Subsets) - Это множественный неименованный инсерт.
Далее вводит колличество элементов в input, выбирает позицию Start в выпадающем списке и нажимает кнопку Ok.

19) ```And I set value "Big multicube" to input "Module Name"```
Шаг введет текст *Big multicube* в инпут у которого атрибут *Name* = Module Name

20) ```And I see value "LAYS" in "Search Input" input```
Проверяет value у инпута с названием Search Input

21) ```Then I see empty value in "Formula Input"```
Проверят что нет никаких данных в инпуте Formula Input

22) ```And I see that the "Grid Context Menu" is open```
Проверка того что контекстное меню вызванное райт кликом по гриду, открылось!
*When I right click on "Col Header(-1:2)"*
*And I see that the "Grid Context Menu" is open*

Так же можно проверить закрыто ли контекстное меню:
```Then I see that the "Context Menu" is closed```

### Скролл
23) ```And I scroll vertical scroller to down``` 
Вертикальный скролл грида проскролится в самый низ. Так-же можно проскролить этим шагом к началу или середине грида - *top* и *middle*

24) ```When I scroll horizontal scroller to end``` 
Горизонтальный скролл в гриде. Можно в начало и середину страницы проскролить - *start* или *middle*

25) ```And I scroll "vertical" "Modal > Dnd Zone(Free) > scroller" by "350" pixels```
Скролл вертикальный на 350px в модальном окне DND зоны с названием Free
```And I scroll "horizontal" "Card of Dashboards(5.2 Вид РИМ) > scroller" by "300" pixels```
Аналогично вертикальному можно сделать и горизонтальный скролл, правда в этом примере у карточки дашборда с определенным названием на 300px.
Сама карточка дашборда и скроллер должен попадать в зону видимости, иначе шаг не сможет проскролить.

26) ```And I see that "horizontal" scroller scrolled by "400" pixels```
```And I see that "vertical" scroller scrolled by "192" pixels```
Шаги по проверке того, где находится скролл по горизонтали и вертикали в гриде.

27) ```And I see that "horizontal" "Card of Dashboards(big list) > scroller" scrolled by "400" pixels```
```And I see that "vertical" "Modal > Tree Menu > scroller" scrolled by "104" pixels```
В этих шагах проверяется конкректный скролл. 


### Буфер обмена
28) ```Then I see that clipboard contains "100"```
```Then I don't see that clipboard contains "100"```
Проверка значений находящихся в буфере обмена или отсуствия значения в буфере

29) ```And I see that clipboard is empty```
Проверка того что буфер обмена пуст

30) ```Given Clipboard is empty```
Очистка буфера.

31) ```And I copy the selection to the clipboard```
Шаг копируте в буфер выделенный текст.. 
Вот несколько примеров:
```
When I click on "Row Header(Text col with data)"
And I see that "Selection Row Header(1:-1)" exists
And I copy the selection to the clipboard
And I see that clipboard contains "333"
And I see that clipboard contains "444"
```
В этом сценарии кликаем на строчку и копируем ее.. выделяются и ячейки этой строки, оттуда и взялись данные в буфере 333 и 444
```
When I click on "Grid Cell(3:0)"
And I press "END" with "SHIFT" with "ALT"
And I copy the selection to the clipboard
```
В этом шаге копируются сразу много выделенных ячеек

32) ```And I fill cells from the clipboard```
Шаг вставляет данные из буфера в выделенную область.

```
And I click on "Grid Cell(79:1)"
And I click on "Grid Cell(103:1)" with SHIFT
And I fill cells from the clipboard
```

Есть еще специфичный похожий шаг
```And I fill cells from the clipboard without waiting```
Он служит для таких же целей, но без внутренней проверки ожидания.
Применяется в связке с функционалом *Apply By Confirmation (ABC)*

33) ```And I paste data from the clipboard```
Шаг по вставке в выделенную область данных из буфера

34) ```And I fill the clipboard from "f:TestEditableModuleData.csv"```
Заполняет буфер обмена из csv файла

35)  ```When I fill the clipboard:
| 100    | 200    | 300    | 400    |
| Text 1 | Text 2 | Text 3 | Text 4 |
| 0.1    | 0.2    | 0.3    | 0.4    |```

Заполняет буфер в виде таблицы из написанного нами контейнера

## Продолжаем
33) ```And I save the current view as "Test View Tab"```
Сохранение новой вьюхи МК. Для этого нужно находиться в нужном МК и шаг Нажмет на кнопку View в toolbar, выберет в выпадающем списке пункт Save As, в появившемся модальном окне запишет название новой вьюхи, все чекбоксы останутся дефолтными и кликнет на кнопку OK

34) ```And I delete view "Test View Tab"```
Удаление вьюхи в которой нужно находится.. Шаг похож на создание вьюхи.. Тоже нажмет кнопку View > Manage Views, в модалке выберется наша вьюха и нажмется кнопка Delete и Ok

35) ```When I change filter "cube 0" to "cube 2"```
Смена фильтра в МК, КТ или на дашборде . В общем первый всретившийся фильтр в DOM дереве изменится с *cube 0* на *cube 2*
Находясь на Дашборде нужно учитывать что там может быть много одинаковых фильтров и шаг поменяет фильтр у первого встретившегося с указанным названием. Менять фильтра у карточек лучше другими шагами: *When I click on "Card Of Dashboards(Cube МК1 с Заказами) > Filter(Forecast)"*

36) ```And I open module "Editable Module"``` - Открывает МК 
```Then I close module "Basic Module"``` - Закрывает МК

37) ```And I open cell dialog with position "2:2"```
Шаг служит для клика по селектору *cellPreEditor* у определенной ячейки,  т.е. нажмет на ячейку и в ней нажмет на три точки если они есть

38) ```When I call the manual backup with hot keys```
Создание бекапа, в этом шаге заложено нажатие клавиш CTRL + S

39) ```When I call recalculate model```
В шаге заложено нажатие клавиши F9. Активирует *Manual Recalculation Model Mode*


### Шаги для Drive Landing
40) ```And I create new model with name "Model 1"```
Создание модели с именем Model 1 находясь в Drive Landing

41) ```And I create new folder with name "Folder 1"```
Создание папки находясь в Drive Landing

42) ```When I delete "E2E Test Model" model```
Удаление модели находясь в Drive Landing и в нужной месте расположения модели

43) ```When I delete "Folder Renamed" folder```
Удаление папки находясь в Drive Landing и в нужной месте расположения модели

44) ```When I rename "test m. f. one" model to "2 test"```
Переименовываем модель

45) ```When I rename "Folder 1" folder to "Folder Renamed"```
Переименовываем папку

46) ```And I copy "E2E Test Model" model```
Создание копии модели. В имени скопированной модели будет присутствовать уникальный хэш

47) And I delete "Line Item 1"
Находясь в гриде в котором можно удалить строку, шаг выделит нужный элемент и удалит его через кнопку в тулбаре

48) ```And I clear value in "Input(newName)"```
Очистка данных в указанном Input

49) ```And I see "Modal > Input(dataType)" with attribute value equal "List"```
Проверка атрибута у определенного Input

50) ```And I see "Grid Cell Editor" with property value equal "VCAR_01_01"```
Проверка проперти у определенного элемента

51) ```Then I set "Enumerated List" to "E-Property" for element "Display Name Property"```
Выбор определенного пункта в выпадающем списке на пересечении строки и колонки. Первый атрибут это Колонка, второй это Самое значение в выпадающем списке, а третий атрибут это Строка













# специфичные шаги
And I don't see element "Card of Dashboards(1.1 Страны) > Loader" now
And I see that "Global Loader" doesn't exist for a long time
    And I reload app
    When I refresh page
    Given I am on the "Drive Landing" page
    Given I am on the "Basic Module" module
    Given I am on the "Dashboard with Data" dashboard


    Given Isolated "E2E Test Model" model
    Given Not isolated "E2E Context Hard Test" model
    Given App as "modeller"
    Then Destroy feature model
    And I clear temp model at current workspace
    And I wait until modal is opened
    And I clear "([^"]*)" input
    And I see that "Tab Header" with text "Half Years" is active
    And I see that "Tab Header" with text "Half Years" is not active
    And I scroll vertical scroller to element ""
    When I scroll kanban vertical scroller to down
    When I scroll kanban horizontal scroller to end

    And I call the context menu with hot keys - Вызов диалогового окна по CTRL + Q
    And I run action "Default Action" - Запуск акшена по кнопке Run в Toolbar

    And I submit the form - Шаг кликает по кнопке Sabmit

    



 And I set to input "Grid Settings Input" value:
      """
      { "defaultCellWidth": 90, "defaultCellHeight": 30 }
      """

Then I see in input "Formula Input" value:
"""
    =	 100+
100+
100
"""
        
Then I see in element "Grid Cell(2:1)" title:
"""
sdfsdfjsd;lkfjsdlkfjsdlkfj sdfsdfsdfaaaaajkhkjhsdfkljsdhflksdjhfksdljfhksdjfh

sdfsdlkfjsdlkfj lksdjf;sdlkjflkjlksdjf skdfjlsdkfjsd;lfjksdlfj dsfjsdlfkjsdf
"""

When I insert elements after "Улицы":
      """
      Материалы
      2.1 Регионы
      """




[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)