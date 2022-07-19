# SPD Тест - Sales Presentation Demo

Этот тест подготавливает модель к работе моделлера.

Строится нужное время, версии, справочники и их зависимости. Следом на основе построенных измерений создаются Мультикубы с определенной структурой и расположением измерений на нужных плоскостях (строки, колонки или фильтра)

Так же вбиваются нужные формулы мультикубов, меняются данные и сравниваются финальные данные грида. 

Тест выполняется в неизолированной модели с созданием бекапа, в конце тест возвращает модель в исходное состояние до запуска теста.

Если требуется построить модель и использовать ее далее, то нужно удалить шаги с ``Restore`` модели, а в начале можно указать чтоб тест запускался в изолированном виде!

```JS
@thread11
Feature: UI - Builder Menu - Dimensions - Time - Tabs

  Scenario: <Service> I prepare environment
    * Start with a no isolated model "E2E SPD"
    * Start as a "modeller"

  Scenario: <1.1> Choose Current Period as Apr 21
    * Create a manual backup with a hotkey
    * Check if "Notification(Start backup model)" exists
    * Check if "Notification(Start backup model)" does not exist
    * Check if "Notification(Your backup was saved successfully)" exists
    * Check if "Notification(Your backup was saved successfully)" does not exist

    * Click on "Header Menu Element(Logs)" in "Header Menu Element(Security Center)"
    * Check if the Grid exists * loaded
    * Check if "Row Header(2, 0:-1)" exists


    * Click on "Header Menu Element(Time)" in "Header Menu Element(Dimensions)"
    * Check if the Grid exists * loaded
    * Click on "Grid Cell(5:0)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Filter Element(Apr 21)" exists
    * Click on "Filter Element(Apr 21)"
    * Check if the elements in the grid match:
      | 5:-1 | Current Month  |  Apr 21 |

  Scenario: <1.2> Confirm selection of Current Detail Period
    * Click on "Header Menu Element(Time)" in "Header Menu Element(Dimensions)"
    * Click on "Toolbar > Button(Apply)"
    * Wait until the modal form is open
    * Click on "Button(Ok)"
    * Check if "Button(Apply)" is disabled


  Scenario: <1.3> Create new version at the end of the list
    * Click on "Header Menu Element(Versions)" in "Header Menu Element(Dimensions)"
    * Check if the Grid exists * loaded
    * Insert elements "Versions" at position "Start":
      """
      Previous Plan
      """

    * Check if the elements in the grid match:
      | 0:-1 | Previous Plan |        |
      | 1:-1 | Actual        |        |
      | 2:-1 | Forecast      | Actual |


  Scenario: <1.4> Rename "Forecast" to "Current Plan"
    * Click on "Row Header(Forecast)"
    * Type "Current Plan"
    * Press "ENTER"
    * Check if the elements in the grid match:
      | 0:-1 | Previous Plan |
      | 1:-1 | Actual        |
      | 2:-1 | Current Plan  |


  Scenario: <1.5> Set SwitchOver of the "Current Plan" onto "May 21"
    * Click on "Grid Cell(2:1)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Tree Menu" exists
    * Type "1 May 21"
    * Click on "Filter Element(1 May 21)"
    * Check if the elements in the grid match:
      | 0:-1 | Previous Plan |        |          |
      | 1:-1 | Actual        |        |          |
      | 2:-1 | Current Plan  | Actual | 1 May 21 |


  Scenario: <1.6> Insert "Бренды" into Lists
    * Click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"
    * Insert elements "Lists" at position "Start":
      """
    Бренды
      """

    * Check if the elements in the grid match:
      | 0:-1 | Бренды |


  Scenario: <1.7> Insert data to the "Бренды"
    * Click on "Header Menu Element(Бренды)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
    * Insert elements "Elements" at position "Start":
      """
      Клинское
      Толстяк
      Балтика
      """

    * Check if the elements in the grid match:
      | 0:-1 | Клинское |
      | 1:-1 | Толстяк  |
      | 2:-1 | Балтика  |


  Scenario: <1.8> Define the Top Level for "Бренды"
    * Click on "Tab Header(Settings)"
    * Type "Total Br*s" into the cell at the intersection of "Бренды" * "Top Level"
    * Click on "Tab Header(Table)"

    * Check if the elements in the grid match:
      | 0:-1 | Total Br*s |
      | 1:-1 | Клинское     |
      | 2:-1 | Толстяк      |
      | 3:-1 | Балтика      |

  Scenario: <1.9> Add more hierarchies into "Lists"
    * Click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"
    * Insert elements "Lists" at position "End":
      """
      Заводы
      Материалы
      2.1 Регионы
      2.2 Клиенты
      """

    * Check if the elements in the grid match:
      | 0:-1 | Бренды      | Total Br*s |
      | 1:-1 | Заводы      |              |
      | 2:-1 | Материалы   |              |
      | 3:-1 | 2.1 Регионы |              |
      | 4:-1 | 2.2 Клиенты |              |


  Scenario: <1.10> Set up the "Заводы" hierarchy
    * Click on "Header Menu Element(Заводы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"

    * Insert elements "Elements" at position "Start":
      """
      Клин
      Курск
      Иваново
      """

    * Click on "Tab Header(Settings)"
    * Type "Total Factories" into the cell at the intersection of "Заводы" * "Top Level"
    * Click on "Tab Header(Table)"
    * Check if the elements in the grid match:
      | 0:-1 | Total Factories |
      | 1:-1 | Клин            |
      | 2:-1 | Курск           |
      | 3:-1 | Иваново         |


  Scenario: <1.11> Set up the "Материалы" hierarchy
    * Click on "Header Menu Element(Материалы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
    * Insert elements "Elements" at position "Start":
      """
      Хмель
      Солод
      Вода
      Соль
      """

    * Click on "Tab Header(Settings)"
    * Type "Total Materials" into the cell at the intersection of "Материалы" * "Top Level"
    * Click on "Tab Header(Table)"
    * Check if the elements in the grid match:
      | 0:-1 | Total Materials |
      | 1:-1 | Хмель           |
      | 2:-1 | Солод           |
      | 3:-1 | Вода            |
      | 4:-1 | Соль            |


  Scenario: <1.12> Set up the "2.1 Регионы" hierarchy
    * Click on "Header Menu Element(2.1 Регионы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
    * Insert elements "Elements" at position "Start":
      """
      Запад
      Центр
      Юг
      Восток
      """

    * Click on "Tab Header(Settings)"
    * Type "Total Company" into the cell at the intersection of "2.1 Регионы" * "Top Level"
    * Click on "Tab Header(Table)"

    * Check if the elements in the grid match:
      | 0:-1 | Total Company |
      | 1:-1 | Запад         |
      | 2:-1 | Центр         |
      | 3:-1 | Юг            |
      | 4:-1 | Восток        |


  Scenario: <1.13> Set up the "2.2 Клиенты" hierarchy
    * Click on "Header Menu Element(2.2 Клиенты)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
    * Insert elements "Elements" at position "Start":
      """
      Лента
      Карусель
      Азбука Вкуса
      Перекресток
      Магнит
      Красное и Белое
      """

    * Check if the elements in the grid match:
      | 0:-1 | Лента           |
      | 1:-1 | Карусель        |
      | 2:-1 | Азбука Вкуса    |
      | 3:-1 | Перекресток     |
      | 4:-1 | Магнит          |
      | 5:-1 | Красное и Белое |


  Scenario: <1.14> Set parent hierarchy for "2.2 Клиенты"
    * Click on "Tab Header(Settings)"
    * Click on "Grid Cell(1:0)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Tree Menu" exists
    * Click on "Filter Element(2.1 Регионы)"
    * Click on "Tab Header(Table)"
    * Check if the elements in the grid match:
      | 0:-1  | Total Company   |
      | 1:-1  | Запад           |
      | 2:-1  | Центр           |
      | 3:-1  | Юг              |
      | 4:-1  | Восток          |
      | 5:-1  | Лента           |
      | 6:-1  | Карусель        |
      | 7:-1  | Азбука Вкуса    |
      | 8:-1  | Перекресток     |
      | 9:-1  | Магнит          |
      | 10:-1 | Красное и Белое |


  Scenario: <1.15> Set parent for the "2.2 Клиенты" elements
    * Click on "Grid Cell(5:2)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Tree Menu" exists
    * Click on "Filter Element(Запад)"

    * Click on "Grid Cell(6:2)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Tree Menu" exists
    * Click on "Filter Element(Запад)"

    * Click on "Grid Cell(7:2)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Tree Menu" exists
    * Click on "Filter Element(Центр)"

    * Click on "Grid Cell(8:2)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Tree Menu" exists
    * Click on "Filter Element(Центр)"

    * Click on "Grid Cell(9:2)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Tree Menu" exists
    * Click on "Filter Element(Юг)"

    * Click on "Grid Cell(10:2)"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Tree Menu" exists
    * Click on "Filter Element(Восток)"


    * Check if the elements in the grid match:
      | 0:-1  | Total Company       | | |               |
      | 1:-1  |   Запад             | | | Total Company |
      | 2:-1  |     Лента           | | | Запад         |
      | 3:-1  |     Карусель        | | | Запад         |
      | 4:-1  |   Центр             | | | Total Company |
      | 5:-1  |     Азбука Вкуса    | | | Центр         |
      | 6:-1  |     Перекресток     | | | Центр         |
      | 7:-1  |   Юг                | | | Total Company |
      | 8:-1  |     Магнит          | | | Юг            |
      | 9:-1  |   Восток            | | | Total Company |
      | 10:-1 |     Красное и Белое | | | Восток        |


  Scenario: <1.16> Check the "Lists" structure
    * Click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"

    * Check if the elements in the grid match:
      | 0:-1 | Бренды      | Total Br*s    |             |
      | 1:-1 | Заводы      | Total Factories |             |
      | 2:-1 | Материалы   | Total Materials |             |
      | 3:-1 | 2.1 Регионы | Total Company   |             |
      | 4:-1 | 2.2 Клиенты |                 | 2.1 Регионы |


  Scenario: <1.17> Create "Functional Areas"
    * Click on "Header Menu Element(Folders)" in "Header Menu Element(Visualization)"
    * Insert elements "Folders" at position "Start":
      """
      Доходы и Расходы
      Финансовый Результат
      """

    * Check if the elements in the grid match:
      | 0:-1 | Доходы и Расходы     |
      | 1:-1 | Финансовый Результат |


  Scenario: <2.1> Create module "Доходы"
    * Click on "Header Menu Element(Multicubes)" in "Header Menu Element(Data)"
    * Click on "Enabled Button(Add Multicube with Name)"
    * Click on "Modal > Button(Place)"
    * Drag "Dnd Zone(Available) > Dnd Element(Versions)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Versions)" exists
    * Drag "Dnd Zone(Available) > Dnd Element(Бренды)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Бренды)" exists
    * Drag "Dnd Zone(Available) > Dnd Element(2.2 Клиенты)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(2.2 Клиенты)" exists

    * Type the text into "Input(Line Items)":
      """
      Продажи
      Upsale
      """

    * Click on "Modal > Tab Header(Advanced)"
    * Type "Доходы" into "Input(New Powercube Name)"
    * Select element "Доходы и Расходы" in "Dropdown(categories)"
    * Check if "Modal > Input(categories)" attribute value equals to "Доходы и Расходы"
    * Click on "Button(Create)"
    * Check if the elements in the grid match:
      | 0:-1 | Продажи |
      | 1:-1 | Upsale  |


  Scenario: <2.2> Insert a Line Item using the Edit Mode
    * Click on "Tab Header(Edit Mode)"
    * Insert elements "Cubes" at position "End":
      """
      Общие доходы
      """

    * Check if the elements in the grid match:
      | 0:-1 | Доходы          |
      | 1:-1 |   Продажи       |
      | 2:-1 |   Upsale        |
      | 3:-1 |   Общие доходы  |


  Scenario: <2.3> Check the module structure
    * Click on "Tab Header(Доходы)"
    * Check if the elements in the grid match:
      | 0:-1 | Продажи       | 0 | 0 | 0 | 0 | 0 | 0 |
      | 1:-1 | Upsale        | 0 | 0 | 0 | 0 | 0 | 0 |
      | 2:-1 | Общие доходы  | 0 | 0 | 0 | 0 | 0 | 0 |

    * Click on "Tab Header(Доходы) > Icon(close)"

  Scenario: <2.4> Create module "Производственные затраты"
    * Click on "Header Menu Element(Add Multicube)" in "Header Menu Element(Data)" in "Header Menu Element(Multicubes)"
    * Check if "Modal" exists
    * Click on "Modal > Button(Place)"
    * Drag "Dnd Zone(Available) > Dnd Element(Versions)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Versions)" exists
    * Drag "Dnd Zone(Available) > Dnd Element(Бренды)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Бренды)" exists
    * Drag "Dnd Zone(Available) > Dnd Element(Заводы)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Заводы)" exists
    * Type the text into "Input(Line Items)":
      """
      Затраты на материалы
      Затраты на изготовление
      Общезаводские затраты
      Себестоимость производства
      """

    * Click on "Modal > Tab Header(Advanced)"
    * Type "Производственные затраты" into "Input(New Powercube Name)"
    * Select element "Доходы и Расходы" in "Dropdown(categories)"
    * Check if "Modal > Input(categories)" attribute value equals to "Доходы и Расходы"
    * Click on "Button(Create)"
    * Check if the elements in the grid match:
      | 0:-1 | Затраты на материалы       |
      | 1:-1 | Затраты на изготовление    |
      | 2:-1 | Общезаводские затраты      |
      | 3:-1 | Себестоимость производства |

    * Click on "Tab Header(Производственные затраты) > Icon(close)"


  Scenario: <2.5> Create module "Накладные расходы"
    * Click on "Header Menu Element(Add Multicube)" in "Header Menu Element(Data)" in "Header Menu Element(Multicubes)"
    * Check if "Modal" exists
    * Click on "Modal > Button(Place)"
    * Drag "Dnd Zone(Available) > Dnd Element(Versions)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Versions)" exists
    * Drag "Dnd Zone(Available) > Dnd Element(Бренды)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Бренды)" exists
    * Type the text into "Input(Line Items)":
      """
      Реклама ТВ
      Затраты на персонал
      Скидки дистрибьюторам
      Общие накладные затраты
      """

    * Click on "Modal > Tab Header(Advanced)"
    * Type "Накладные расходы" into "Input(New Powercube Name)"
    * Select element "Доходы и Расходы" in "Dropdown(categories)"
    * Check if "Modal > Input(categories)" attribute value equals to "Доходы и Расходы"
    * Click on "Button(Create)"
    * Check if the elements in the grid match:
      | 0:-1 | Реклама ТВ              |
      | 1:-1 | Затраты на персонал     |
      | 2:-1 | Скидки дистрибьюторам   |
      | 3:-1 | Общие накладные затраты |

    * Click on "Tab Header(Накладные расходы) > Icon(close)"


  Scenario: <2.6> Create module "Фин. результат"
    * Click on "Header Menu Element(Add Multicube)" in "Header Menu Element(Data)" in "Header Menu Element(Multicubes)"
    * Check if "Modal" exists
    * Click on "Modal > Button(Place)"
    * Drag "Dnd Zone(Available) > Dnd Element(Versions)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Versions)" exists
    * Drag "Dnd Zone(Available) > Dnd Element(Бренды)" * drop after "Dnd Element(Filters)"
    * Check if "Dnd Zone(Selected) > Dnd Element(Бренды)" exists
    * Type the text into "Input(Line Items)":
      """
      Доходы
      Заводские расходы
      Накладные расходы
      Чистая прибыль
      Налог
      Дивиденды
      """

    * Click on "Modal > Tab Header(Advanced)"
    * Type "Фин. результат" into "Input(New Powercube Name)"
    * Click on "Button(Create)"
    * Check if the elements in the grid match:
      | 0:-1 | Доходы            |
      | 1:-1 | Заводские расходы |
      | 2:-1 | Накладные расходы |
      | 3:-1 | Чистая прибыль    |
      | 4:-1 | Налог             |
      | 5:-1 | Дивиденды         |

    * Click on "Tab Header(Фин. результат) > Icon(close)"

  Scenario: <3.1> Change view for "Доходы"
    * Click on "Contents Element(Доходы)"
    * Check if the Grid exists * loaded
    * Click on "Toolbar > Enabled Button(Pivot)"

    * Drag "Dnd Element(Versions)" * drop after "Dnd Element(Cubes)"
    * Check if "Dnd Zone(Rows) > Dnd Element(Versions)" exists
    * Drag "Dnd Element(2.2 Клиенты)" * drop into "Dnd Zone(Pages)"
    * Check if "Dnd Zone(Pages) > Dnd Element(2.2 Клиенты)" exists
    * Drag "Dnd Element(Бренды)" * drop into "Dnd Zone(Pages)"
    * Check if "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    * Click on "Button(Ok)"

    * Check if the elements in the grid match:
      | 0:-1 | Продажи       | 0 | 0 | 0 |
      | 1:-1 | Upsale        | 0 | 0 | 0 |
      | 2:-1 | Общие доходы  | 0 | 0 | 0 |
      | 3:-1 | Продажи       | 0 | 0 | 0 |
      | 4:-1 | Upsale        | 0 | 0 | 0 |
      | 5:-1 | Общие доходы  | 0 | 0 | 0 |
      | 6:-1 | Продажи       | 0 | 0 | 0 |
      | 7:-1 | Upsale        | 0 | 0 | 0 |
      | 8:-1 | Общие доходы  | 0 | 0 | 0 |


  Scenario: <3.2> Save current view as default view for "Доходы"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save)"
    * Check if "Modal" exists
    * Click on "Modal > Button(Ok)"
    * Check if "Modal" does not exist

    * Reload Page
    * Check if "Global Loader" exists
    * Check if "Tab Header" with text "Доходы" is active
    * Check if "Any Loader" does not exist
    * Check if "Filter(Total Company)" exists
    * Check if the elements in the grid match:
      | 0:-1 | Продажи       | 0 | 0 | 0 |
      | 1:-1 | Upsale        | 0 | 0 | 0 |
      | 2:-1 | Общие доходы  | 0 | 0 | 0 |
      | 3:-1 | Продажи       | 0 | 0 | 0 |
      | 4:-1 | Upsale        | 0 | 0 | 0 |
      | 5:-1 | Общие доходы  | 0 | 0 | 0 |
      | 6:-1 | Продажи       | 0 | 0 | 0 |
      | 7:-1 | Upsale        | 0 | 0 | 0 |
      | 8:-1 | Общие доходы  | 0 | 0 | 0 |


  Scenario: <3.3> Create "Доходы - Лента" view
    * Click on "Toolbar > Enabled Button(Pivot)"
    * Drag "Dnd Element(Бренды)" * drop into "Dnd Zone(Rows)"
    * Check if "Dnd Zone(Rows) > Dnd Element(Бренды)" exists
    * Click on "Button(Ok)"
    * Check if "Filter(Total Company)" exists
    * Check if the elements in the grid match:
      | 0:-1  | Total Br*s | 0 | 0 |
      | 1:-1  |   Клинское   | 0 | 0 |
      | 2:-1  |   Толстяк    | 0 | 0 |
      | 3:-1  |   Балтика    | 0 | 0 |
      | 4:-1  | Total Br*s | 0 | 0 |
      | 5:-1  |   Клинское   | 0 | 0 |
      | 6:-1  |   Толстяк    | 0 | 0 |
      | 7:-1  |   Балтика    | 0 | 0 |

  Scenario: <3.4> "Save As..." the view "Доходы - Лента"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save As)"
    * Check if "Modal" exists
    * Type "Доходы - Лента" into "Input(New View Name)"
    * Check if "Modal > Radio Button(New)" is checked
    * Check if "Modal > Checkbox(Model Global View)" is checked
    * Click on "Button(Ok)"
    * Check if "Contents Element(Доходы - Лента)" exists

    * Reload Page
    * Check if "Global Loader" exists
    * Check if "Tab Header" with text "Доходы - Лента" is active
    * Check if "Any Loader" does not exist
    * Check if "Filter(Total Company)" exists

  Scenario: <3.5> Change view for "Накладные расходы"
    * Click on "Contents Element(Накладные расходы)"
    * Check if the Grid exists * loaded
    * Click on "Enabled Button(Pivot)"
    * Drag "Dnd Element(Versions)" * drop before "Dnd Element(Cubes)"
    * Check if "Dnd Zone(Rows) > Dnd Element(Versions)" exists
    * Drag "Dnd Element(Бренды)" * drop into "Dnd Zone(Pages)"
    * Check if "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    * Click on "Button(Ok)"
    * Check if the elements in the grid match:
      | 0:-1  | Реклама ТВ              | 0 | 0 |
      | 1:-1  | Затраты на персонал     | 0 | 0 |
      | 2:-1  | Скидки дистрибьюторам   | 0 | 0 |
      | 3:-1  | Общие накладные затраты | 0 | 0 |
      | 4:-1  | Реклама ТВ              | 0 | 0 |
      | 5:-1  | Затраты на персонал     | 0 | 0 |
      | 6:-1  | Скидки дистрибьюторам   | 0 | 0 |
      | 7:-1  | Общие накладные затраты | 0 | 0 |

  Scenario: <3.6> Save current view as default view for "Накладные расходы"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save)"
    * Check if "Modal" exists
    * Click on "Modal > Button(Ok)"
    * Check if "Modal" does not exist
    * Click on "Tab Header(Накладные расходы) > Icon(close)"

    * Click on "Contents Element(Накладные расходы)"
    * Check if "Filter(Total Br*s)" exists
    * Check if the elements in the grid match:
      | 0:-1  | Реклама ТВ              | 0 | 0 |
      | 1:-1  | Затраты на персонал     | 0 | 0 |
      | 2:-1  | Скидки дистрибьюторам   | 0 | 0 |
      | 3:-1  | Общие накладные затраты | 0 | 0 |
      | 4:-1  | Реклама ТВ              | 0 | 0 |
      | 5:-1  | Затраты на персонал     | 0 | 0 |
      | 6:-1  | Скидки дистрибьюторам   | 0 | 0 |
      | 7:-1  | Общие накладные затраты | 0 | 0 |
      | 8:-1  | Реклама ТВ              | 0 | 0 |
      | 9:-1  | Затраты на персонал     | 0 | 0 |
      | 10:-1 | Скидки дистрибьюторам   | 0 | 0 |
      | 11:-1 | Общие накладные затраты | 0 | 0 |


  Scenario: <3.7> Create "Накладные расходы - Клинское" view
    * Change the filter from "Total Br*s" to "Клинское"
    * Check if the elements in the grid match:
      | 0:-1  | Реклама ТВ              | 0 | 0 |
      | 1:-1  | Затраты на персонал     | 0 | 0 |
      | 2:-1  | Скидки дистрибьюторам   | 0 | 0 |
      | 3:-1  | Общие накладные затраты | 0 | 0 |
      | 4:-1  | Реклама ТВ              | 0 | 0 |
      | 5:-1  | Затраты на персонал     | 0 | 0 |
      | 6:-1  | Скидки дистрибьюторам   | 0 | 0 |
      | 7:-1  | Общие накладные затраты | 0 | 0 |
      | 8:-1  | Реклама ТВ              | 0 | 0 |
      | 9:-1  | Затраты на персонал     | 0 | 0 |
      | 10:-1 | Скидки дистрибьюторам   | 0 | 0 |
      | 11:-1 | Общие накладные затраты | 0 | 0 |


  Scenario: <3.8> "Save As..." the view "Накладные расходы - Клинское"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save As)"
    * Check if "Modal" exists
    * Type "Накладные расходы - Клинское" into "Input(New View Name)"
    * Check if "Modal > Radio Button(New)" is checked
    * Check if "Modal > Checkbox(Model Global View)" is checked
    * Click on "Button(Ok)"
    * Check if "Contents Element(Накладные расходы - Клинское)" exists
    * Click on "Tab Header(Накладные расходы - Клинское) > Icon(close)"


  Scenario: <3.9> Change view for "Производственные затраты"
    * Click on "Contents Element(Производственные затраты)"
    * Check if the Grid exists * loaded
    * Click on "Enabled Button(Pivot)"
    * Drag "Dnd Element(Versions)" * drop before "Dnd Element(Cubes)"
    * Check if "Dnd Zone(Rows) > Dnd Element(Versions)" exists
    * Drag "Dnd Element(Заводы)" * drop into "Dnd Zone(Pages)"
    * Check if "Dnd Zone(Pages) > Dnd Element(Заводы)" exists
    * Drag "Dnd Element(Бренды)" * drop into "Dnd Zone(Pages)"
    * Check if "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    * Click on "Button(Ok)"
    * Check if the elements in the grid match:
      | 0:-1  | Затраты на материалы       | 0 | 0 |
      | 1:-1  | Затраты на изготовление    | 0 | 0 |
      | 2:-1  | Общезаводские затраты      | 0 | 0 |
      | 3:-1  | Себестоимость производства | 0 | 0 |
      | 4:-1  | Затраты на материалы       | 0 | 0 |
      | 5:-1  | Затраты на изготовление    | 0 | 0 |
      | 6:-1  | Общезаводские затраты      | 0 | 0 |
      | 7:-1  | Себестоимость производства | 0 | 0 |


  Scenario: <3.10> Save current view as default view for "Производственные затраты"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save)"
    * Check if "Modal" exists
    * Click on "Modal > Button(Ok)"
    * Check if "Modal" does not exist
    * Click on "Tab Header(Производственные затраты) > Icon(close)"
    * Click on "Contents Element(Производственные затраты)"
    * Check if "Filter(Total Factories)" exists
    * Check if the elements in the grid match:
      | 0:-1  | Затраты на материалы       | 0 | 0 |
      | 1:-1  | Затраты на изготовление    | 0 | 0 |
      | 2:-1  | Общезаводские затраты      | 0 | 0 |
      | 3:-1  | Себестоимость производства | 0 | 0 |
      | 4:-1  | Затраты на материалы       | 0 | 0 |
      | 5:-1  | Затраты на изготовление    | 0 | 0 |
      | 6:-1  | Общезаводские затраты      | 0 | 0 |
      | 7:-1  | Себестоимость производства | 0 | 0 |


  Scenario: <3.11> Create "Клин - Клинское" view
    * Change the filter from "Total Factories" to "Клин"
    * Change the filter from "Total Br*s" to "Клинское"
    * Check if the elements in the grid match:
      | 0:-1  | Затраты на материалы       | 0 | 0 |
      | 1:-1  | Затраты на изготовление    | 0 | 0 |
      | 2:-1  | Общезаводские затраты      | 0 | 0 |
      | 3:-1  | Себестоимость производства | 0 | 0 |
      | 4:-1  | Затраты на материалы       | 0 | 0 |
      | 5:-1  | Затраты на изготовление    | 0 | 0 |
      | 6:-1  | Общезаводские затраты      | 0 | 0 |
      | 7:-1  | Себестоимость производства | 0 | 0 |


  Scenario: <3.12> "Save As..." the view "Клин - Клинское"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save As)"
    * Check if "Modal" exists
    * Type "Клин - Клинское" into "Input(New View Name)"
    * Check if "Modal > Radio Button(New)" is checked
    * Check if "Modal > Checkbox(Model Global View)" is checked
    * Click on "Button(Ok)"
    * Check if "Contents Element(Клин - Клинское)" exists
    * Click on "Tab Header(Клин - Клинское) > Icon(close)"


  Scenario: <3.13> Change view for "Фин. результат"
    * Click on "Contents Element(Фин. результат)"
    * Check if the Grid exists * loaded
    * Click on "Enabled Button(Pivot)"

    * Drag "Dnd Element(Versions)" * drop before "Dnd Element(Cubes)"
    * Check if "Dnd Zone(Rows) > Dnd Element(Versions)" exists

    * Drag "Dnd Element(Бренды)" * drop before "Dnd Element(Cubes)"
    * Check if "Dnd Zone(Rows) > Dnd Element(Бренды)" exists
    * Click on "Button(Ok)"

    * Check if the elements in the grid match:
      |  0:-1 | Доходы            | 0 | 0 |
      |  1:-1 | Заводские расходы | 0 | 0 |
      |  2:-1 | Накладные расходы | 0 | 0 |
      |  3:-1 | Чистая прибыль    | 0 | 0 |
      |  4:-1 | Налог             | 0 | 0 |
      |  5:-1 | Дивиденды         | 0 | 0 |
      |  6:-1 | Доходы            | 0 | 0 |
      |  7:-1 | Заводские расходы | 0 | 0 |
      |  8:-1 | Накладные расходы | 0 | 0 |
      |  9:-1 | Чистая прибыль    | 0 | 0 |
      | 10:-1 | Налог             | 0 | 0 |
      | 11:-1 | Дивиденды         | 0 | 0 |


  Scenario: <3.14> Save current view as default view for "Фин. результат"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save)"
    * Check if "Modal" exists
    * Click on "Modal > Button(Ok)"
    * Check if "Modal" does not exist
    * Click on "Tab Header(Фин. результат) > Icon(close)"
    * Click on "Contents Element(Фин. результат)"
    * Check if the elements in the grid match:
      |  0:-1 | Доходы            | 0 | 0 |
      |  1:-1 | Заводские расходы | 0 | 0 |
      |  2:-1 | Накладные расходы | 0 | 0 |
      |  3:-1 | Чистая прибыль    | 0 | 0 |
      |  4:-1 | Налог             | 0 | 0 |
      |  5:-1 | Дивиденды         | 0 | 0 |
      |  6:-1 | Доходы            | 0 | 0 |
      |  7:-1 | Заводские расходы | 0 | 0 |
      |  8:-1 | Накладные расходы | 0 | 0 |
      |  9:-1 | Чистая прибыль    | 0 | 0 |
      | 10:-1 | Налог             | 0 | 0 |
      | 11:-1 | Дивиденды         | 0 | 0 |


  Scenario: <3.15> Hide Jun 21 column
    * Right click on "Col Header(Jun 21)"
    * Click on "Menu Item(Hide)"
    * Check if the Grid exists * loaded
    * Check if "Col Header(Jul 21)" exists
    * Check if "Col Header(Jun 21)" does not exist

  Scenario: <3.16> Hide Jul 21 column
    * Right click on "Col Header(Jul 21)"
    * Click on "Menu Item(Hide)"
    * Check if the Grid exists * loaded
    * Check if "Col Header(Aug 21)" exists
    * Check if "Col Header(Jul 21)" does not exist

  Scenario: <3.17> Hide Aug 21 column
    * Right click on "Col Header(Aug 21)"
    * Click on "Menu Item(Hide)"
    * Check if the Grid exists * loaded
    * Check if "Col Header(Sep 21)" exists
    * Check if "Col Header(Aug 21)" does not exist

  Scenario: <3.18> Hide Sep 21 column
    * Right click on "Col Header(Sep 21)"
    * Click on "Menu Item(Hide)"
    * Check if the Grid exists * loaded
    * Check if "Col Header(Oct 21)" exists
    * Check if "Col Header(Sep 21)" does not exist

  Scenario: <3.19> Hide Oct 21 column
    * Right click on "Col Header(Oct 21)"
    * Click on "Menu Item(Hide)"
    * Check if the Grid exists * loaded
    * Check if "Col Header(Nov 21)" exists
    * Check if "Col Header(Oct 21)" does not exist

  Scenario: <3.20> Hide Nov 21 column
    * Right click on "Col Header(Nov 21)"
    * Click on "Menu Item(Hide)"
    * Check if the Grid exists * loaded
    * Check if "Col Header(Dec 21)" exists
    * Check if "Col Header(Nov 21)" does not exist

  Scenario: <3.21> Hide Dec 21 column
    * Right click on "Col Header(Dec 21)"
    * Click on "Menu Item(Hide)"
    * Check if the Grid exists * loaded
    * Check if "Col Header(FY21)" exists
    * Check if "Col Header(Dec 21)" does not exist

  Scenario: <3.22> Unselect details-level "Бренды"
    * Click on "Button(Pivot)"
    * Drag "Dnd Element(Бренды)" * drop after "Dnd Element(Cubes)"
    * Click on "Button(Ok)"
    * Check if "Row Header(Клинское)" exists

    * Click on "Row Header(0:-1)"
    * Right click on "Row Header(0:-1)"
    * Click on "Menu Item(Select Level to Show...)"
    * Check if "Modal > Checkbox(details)" is checked
    * Click on "Modal > Checkbox(details)"
    * Click on "Modal > Button(Ok)"
    * Check if the Grid exists * loaded
    * Check if "Row Header(Клинское)" does not exist

    * Click on "Row Header(0:-1)"
    * Right click on "Row Header(0:-1)"
    * Click on "Menu Item(Reselect Level)"
    * Wait until the modal form is open

    * Check if "Modal > Checkbox(details)" is not checked
    * Click on "Modal > Button(Cancel)"

  Scenario: <3.23> Create "Data Input Check" view
    * Click on "Button(Pivot)"
    * Wait until the modal form is open
    * Drag "Dnd Element(Cubes)" * drop after "Dnd Element(Бренды)"
    * Click on "Button(Ok)"
    * Check if the elements in the grid match:
      |  0:-1 | Доходы            | 0 | 0 |
      |  1:-1 | Заводские расходы | 0 | 0 |
      |  2:-1 | Накладные расходы | 0 | 0 |
      |  3:-1 | Чистая прибыль    | 0 | 0 |
      |  4:-1 | Налог             | 0 | 0 |
      |  5:-1 | Дивиденды         | 0 | 0 |
      |  6:-1 | Доходы            | 0 | 0 |
      |  7:-1 | Заводские расходы | 0 | 0 |
      |  8:-1 | Накладные расходы | 0 | 0 |
      |  9:-1 | Чистая прибыль    | 0 | 0 |
      | 10:-1 | Налог             | 0 | 0 |
      | 11:-1 | Дивиденды         | 0 | 0 |
      | 12:-1 | Доходы            | 0 | 0 |
      | 13:-1 | Заводские расходы | 0 | 0 |
      | 14:-1 | Накладные расходы | 0 | 0 |
      | 15:-1 | Чистая прибыль    | 0 | 0 |
      | 16:-1 | Налог             | 0 | 0 |
      | 17:-1 | Дивиденды         | 0 | 0 |


  Scenario: <3.24> "Save As..." the view "Data Input Check"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save As)"
    * Check if "Modal" exists
    * Type "Data Input Check" into "Input(New View Name)"
    * Check if "Modal > Radio Button(New)" is checked
    * Check if "Modal > Checkbox(Model Global View)" is checked
    * Click on "Button(Ok)"
    * Check if "Contents Element(Data Input Check)" exists
    * Click on "Tab Header(Data Input Check) > Icon(close)"


  Scenario: <4.1> Open "Доходы" * enter Edit Mode
    * Click on "Contents Element(Доходы)"
    * Check if the Grid exists * loaded
    * Click on "Tab Header(Edit Mode)"
    * Check if the elements in the grid match:
      | 0:-1 | Доходы          |
      | 1:-1 |   Продажи       |
      | 2:-1 |   Upsale        |
      | 3:-1 |   Общие доходы  |

  Scenario: <4.2> Enter formulas for "Доходы"
    * Type "'Продажи' * 0.1" into the cell at the intersection of "Formula" * "Upsale"
    * Type "'Продажи' + 'Upsale'" into the cell at the intersection of "Formula" * "Общие доходы"
    * Check if the elements in the grid match:
      | 0:-1 | Доходы          |  |                  |
      | 1:-1 |   Продажи       |  |                  |


  Scenario: <4.3> Check the module structure
    * Click on "Tab Header(Доходы)"
    * Check if the elements in the grid match:
      | 0:-1 | Продажи      | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
      | 1:-1 | Upsale       | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
      | 2:-1 | Общие доходы | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
      | 3:-1 | Продажи      | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
      | 4:-1 | Upsale       | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
      | 5:-1 | Общие доходы | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
      | 6:-1 | Продажи      | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
      | 7:-1 | Upsale       | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
      | 8:-1 | Общие доходы | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |


  Scenario: <4.4> Fill formulas for the new modules
    * Click on "Header Menu Element(Cubes)" in "Header Menu Element(Data)"
    * Check if the Grid exists * loaded
    * Type "1000 + 'Затраты на изготовление' * 0.1" into the cell at the intersection of "Formula" * "Общезаводские затраты"
    * Type "'Затраты на материалы' + 'Затраты на изготовление' + 'Общезаводские затраты'" into the cell at the intersection of "Formula" * "Себестоимость производства"
    * Type "'Доходы'.'Продажи' * 0.05" into the cell at the intersection of "Formula" * "Реклама ТВ"
    * Type "600 + 'Производственные затраты'.'Затраты на изготовление' * 0.4" into the cell at the intersection of "Formula" * "Затраты на персонал"
    * Type "'Реклама ТВ' + 'Затраты на персонал' + 'Скидки дистрибьюторам'" into the cell at the intersection of "Formula" * "Общие накладные затраты"

    * Type "'Доходы'.'Общие доходы'" into the cell at the intersection of "Formula" * the row number [15]
    * Type "'Производственные затраты'.'Себестоимость производства' * 1.1" into the cell at the intersection of "Formula" * "Заводские расходы"
    * Type "'Накладные расходы'.'Общие накладные затраты'" into the cell at the intersection of "Formula" * the row number [17]
    * Type "'Доходы' - 'Заводские расходы' - 'Накладные расходы'" into the cell at the intersection of "Formula" * "Чистая прибыль"
    * Type "IF 'Чистая прибыль' > 0 * 'Чистая прибыль' * 0.24 ELSE 0" into the cell at the intersection of "Formula" * "Налог"
    * Type "('Чистая прибыль' - 'Налог') * 0.3" into the cell at the intersection of "Formula" * "Дивиденды"
    * Check if the elements in the grid match:
      | 0:-1 | Доходы                       |  |                                                                              |
      | 1:-1 |   Продажи                    |  |                                                                              |
      | 2:-1 |   Upsale                     |  | 'Продажи' * 0.1                                                              |
      | 3:-1 |   Общие доходы               |  | 'Продажи' + 'Upsale'                                                         |
      | 4:-1 | Производственные затраты     |  |                                                                              |
      | 5:-1 |   Затраты на материалы       |  |                                                                              |
      | 6:-1 |   Затраты на изготовление    |  |                                                                              |
      | 7:-1 |   Общезаводские затраты      |  | 1000 + 'Затраты на изготовление' * 0.1                                       |
      | 8:-1 |   Себестоимость производства |  | 'Затраты на материалы' + 'Затраты на изготовление' + 'Общезаводские затраты' |
      | 9:-1 | Накладные расходы            |  |                                                                              |
      | 10:-1 |   Реклама ТВ                |  | 'Доходы'.'Продажи' * 0.05                                                    |
      | 11:-1 |   Затраты на персонал       |  | 600 + 'Производственные затраты'.'Затраты на изготовление' * 0.4             |
      | 12:-1 |   Скидки дистрибьюторам     |  |                                                                              |
      | 13:-1 |   Общие накладные затраты   |  | 'Реклама ТВ' + 'Затраты на персонал' + 'Скидки дистрибьюторам'               |
      | 14:-1 | Фин. результат              |  |                                                                              |
      | 15:-1 |   Доходы                    |  | 'Доходы'.'Общие доходы'                                                      |
      | 16:-1 |   Заводские расходы         |  | 'Производственные затраты'.'Себестоимость производства' * 1.1                |
      | 17:-1 |   Накладные расходы         |  | 'Накладные расходы'.'Общие накладные затраты'                                |
      | 18:-1 |   Чистая прибыль            |  | 'Доходы' - 'Заводские расходы' - 'Накладные расходы'                         |
      | 19:-1 |   Налог                     |  | IF 'Чистая прибыль' > 0 * 'Чистая прибыль' * 0.24 ELSE 0                  |
      | 20:-1 |   Дивиденды                 |  | ('Чистая прибыль' - 'Налог') * 0.3                                           |


  Scenario: <4.5> Select style for "Чистая прибыль"
    * Click on "Grid Cell(18:16 )"
    * Click on "Cell Pre Editor > Icon(arrow_drop_down)"
    * Check if "Filter Element(Summary2)" exists
    * Click on "Filter Element(Summary2)"
    * Check if "Grid Cell(18:16, Summary2)" exists

  Scenario: <4.6> Control Check 0 (checking final results in "Data Input Check")
    * Click on "Contents Element(Data Input Check)"
    * Check if the Grid exists * loaded
    * Check if the elements in the grid match:
      | 0:-1  | Доходы            | 0       | 0       | 0       | 0       | 0       | 0        |
      | 1:-1  | Заводские расходы | 9 900   | 9 900   | 9 900   | 9 900   | 9 900   | 118 800  |
      | 2:-1  | Накладные расходы | 1 800   | 1 800   | 1 800   | 1 800   | 1 800   | 21 600   |
      | 3:-1  | Чистая прибыль    | -11 700 | -11 700 | -11 700 | -11 700 | -11 700 | -140 400 |
      | 4:-1  | Налог             | 0       | 0       | 0       | 0       | 0       | 0        |
      | 5:-1  | Дивиденды         | -3 510  | -3 510  | -3 510  | -3 510  | -3 510  | -42 120  |
      | 6:-1  | Доходы            | 0       | 0       | 0       | 0       | 0       | 0        |
      | 7:-1  | Заводские расходы | 9 900   | 9 900   | 9 900   | 9 900   | 9 900   | 118 800  |
      | 8:-1  | Накладные расходы | 1 800   | 1 800   | 1 800   | 1 800   | 1 800   | 21 600   |
      | 9:-1  | Чистая прибыль    | -11 700 | -11 700 | -11 700 | -11 700 | -11 700 | -140 400 |
      | 10:-1 | Налог             | 0       | 0       | 0       | 0       | 0       | 0        |
      | 11:-1 | Дивиденды         | -3 510  | -3 510  | -3 510  | -3 510  | -3 510  | -42 120  |
      | 12:-1 | Доходы            | 0       | 0       | 0       | 0       | 0       | 0        |
      | 13:-1 | Заводские расходы | 9 900   | 9 900   | 9 900   | 9 900   | 9 900   | 118 800  |
      | 14:-1 | Накладные расходы | 1 800   | 1 800   | 1 800   | 1 800   | 1 800   | 21 600   |
      | 15:-1 | Чистая прибыль    | -11 700 | -11 700 | -11 700 | -11 700 | -11 700 | -140 400 |
      | 16:-1 | Налог             | 0       | 0       | 0       | 0       | 0       | 0        |
      | 17:-1 | Дивиденды         | -3 510  | -3 510  | -3 510  | -3 510  | -3 510  | -42 120  |


  Scenario: <4.7> Open * "Доходы - Лента" fill row "Продажи"
    * Click on "Contents Element(Доходы - Лента)"
    * Change the filter from "Total Company" to "Лента"
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Save)"
    * Check if "Modal" exists
    * Click on "Modal > Button(Ok)"
    * Check if "Modal" does not exist
    * Check if the Grid exists * loaded
    * Type "100" into the cell at the intersection of "Jan 21" * the row number [1]
    * Check if "Grid Cell(1:0, 100)" exists
    * Click on "Grid Cell (1:0)"
    * Click on "Enabled Button(Copy Right)"
    * Check if "Grid Cell(1:1, 100)" exists
    * Check if the elements in the grid match:
      | 0:-1  | Total Br*s | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
      | 1:-1  | Клинское     | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
      | 2:-1  | Толстяк      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 3:-1  | Балтика      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 4:-1  | Total Br*s | 10  | 10  | 10  | 10  | 10  | 10  | 10  | 10  |
      | 5:-1  | Клинское     | 10  | 10  | 10  | 10  | 10  | 10  | 10  | 10  |
      | 6:-1  | Толстяк      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 7:-1  | Балтика      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 8:-1  | Total Br*s | 110 | 110 | 110 | 110 | 110 | 110 | 110 | 110 |
      | 9:-1  | Клинское     | 110 | 110 | 110 | 110 | 110 | 110 | 110 | 110 |
      | 10:-1 | Толстяк      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 11:-1 | Балтика      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |


  Scenario: <4.8> Change the pivot
    * Click on "Button(Pivot)"
    * Drag "Dnd Element(Бренды)" * drop into "Dnd Zone(Pages)"
    * Check if "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    * Click on "Button(Ok)"
    * Change the filter from "Total Br*s" to "Клинское"
    * Change the filter from "Total Company" to "Лента"
    * Check if the elements in the grid match:
      | 0:-1 | Продажи      | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
      | 1:-1 | Upsale       | 10  | 10  | 10  | 10  | 10  | 10  | 10  | 10  |
      | 2:-1 | Общие доходы | 110 | 110 | 110 | 110 | 110 | 110 | 110 | 110 |
      | 3:-1 | Продажи      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 4:-1 | Upsale       | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 5:-1 | Общие доходы | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 6:-1 | Продажи      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 7:-1 | Upsale       | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 8:-1 | Общие доходы | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |


  Scenario: <4.9> Fill in more cells for Current Plan * Previous Plan
    * Type "0" into the cell at the intersection of "May 21" * the row number [0]
    * Check if "Grid Cell(0:4, 0)" exists
    * Click on "Grid Cell (0:4)"
    * Click on "Enabled Button(Copy Right)"
    * Check if "Grid Cell(0:5, 0)" exists

    * Type "150" into the cell at the intersection of "May 21" * the row number [3]
    * Check if "Grid Cell(3:4, 150)" exists
    * Click on "Grid Cell (3:4)"
    * Click on "Enabled Button(Copy Right)"
    * Check if "Grid Cell(3:5, 150)" exists
    * Check if the elements in the grid match:
      | 0:-1 | Продажи      | 100 | 100 | 100 | 100 | 0   | 0   | 0   | 0   |
      | 1:-1 | Upsale       | 10  | 10  | 10  | 10  | 0   | 0   | 0   | 0   |
      | 2:-1 | Общие доходы | 110 | 110 | 110 | 110 | 0   | 0   | 0   | 0   |
      | 3:-1 | Продажи      | 0   | 0   | 0   | 0   | 150 | 150 |150  | 150 |
      | 4:-1 | Upsale       | 0   | 0   | 0   | 0   | 15  | 15  | 15  | 15  |
      | 5:-1 | Общие доходы | 0   | 0   | 0   | 0   | 165 | 165 |165  | 165 |
      | 6:-1 | Продажи      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 7:-1 | Upsale       | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 8:-1 | Общие доходы | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |


  Scenario: <4.10> Control Check 1 (checking final results in "Data Input Check")
    * Click on "Contents Element(Data Input Check)"
    * Check if the Grid exists * loaded
    * Check if the elements in the grid match:
      | 0:-1  | Доходы            | 110       | 110       | 110       | 110       | 0         | 440        | 440       | 0         |
      | 1:-1  | Заводские расходы | 9 900     | 9 900     | 9 900     | 9 900     | 9 900     | 118 800    | 39 600    | 79 200    |
      | 2:-1  | Накладные расходы | 1 805     | 1 805     | 1 805     | 1 805     | 1 800     | 21 620     | 7 220     | 14 400    |
      | 3:-1  | Чистая прибыль    | -11 595   | -11 595   | -11 595   | -11 595   | -11 700   | -139 980   | -46 380   | -93 600   |
      | 4:-1  | Налог             | 0         | 0         | 0         | 0         | 0         | 0          | 0         | 0         |
      | 5:-1  | Дивиденды         | -3 478    | -3 478    | -3 478    | -3 478    | -3 510    | -41 994    | -13 914   | -28 080   |
      | 6:-1  | Доходы            | 0         | 0         | 0         | 0         | 165       | 1 320      | 0         | 1 320     |
      | 7:-1  | Заводские расходы | 9 900     | 9 900     | 9 900     | 9 900     | 9 900     | 118 800    | 39 600    | 79 200    |
      | 8:-1  | Накладные расходы | 1 800     | 1 800     | 1 800     | 1 800     | 1 808     | 21 660     | 7 200     | 14 460    |


  Scenario: <4.11> Continue filling in "Доходы - Лента"
    * Click on "Contents Element(Доходы)"
    * Check if the Grid exists * loaded
    * Change the filter from "Total Company" to "Лента"
    * Change the filter from "Total Br*s" to "Клинское"
    * Check if the Grid exists * loaded
    * Click on "Grid Cell(0:0)"
    * Type "15000" into the cell at the intersection of "Jan 21" * the row number [0]
    * Check if the elements in the grid match:
      | 0:-1 | Продажи      | 15 000 |

    * Type "16000" into the cell at the intersection of "Feb 21" * the row number [0]
    * Check if the elements in the grid match:
      | 0:-1 | Продажи      | 15 000 | 16 000 |

    * Type "15000" into the cell at the intersection of "Mar 21" * the row number [0]
    * Check if the elements in the grid match:
      | 0:-1 | Продажи      | 15 000 | 16 000 | 15 000 |

    * Type "18500" into the cell at the intersection of "Apr 21" * the row number [0]
    * Check if the elements in the grid match:
      | 0:-1 | Продажи      | 15 000 | 16 000 | 15 000 | 18 500 |

    * Type "18000" into the cell at the intersection of "May 21" * the row number [3]
    * Check if the elements in the grid match:
      | 3:-1 | Продажи      |  |  |  |  | 18 000 |

    * Click on "Grid Cell(3:4)"
    * Click on "Button(Copy Right)"
    * Check if the elements in the grid match:
      | 3:-1 | Продажи      |  |  |  |  | 18 000 | 18 000 |

  Scenario: <4.12> Control Check 2 (checking final results in "Data Input Check")
    * Click on "Contents Element(Data Input Check)"
    * Check if the Grid exists * loaded
    * Check if the elements in the grid match:
      | 0:-1  | Доходы            | 16 500  | 17 600  | 16 500  | 20 350  | 0         | 70 950    | 70 950   | 0         |
      | 1:-1  | Заводские расходы | 9 900   | 9 900   | 9 900   | 9 900   | 9 900     | 118 800   | 39 600   | 79 200    |
      | 2:-1  | Накладные расходы | 2 550   | 2 600   | 2 550   | 2 725   | 1 800     | 24 825    | 10 425   | 14 400    |
      | 3:-1  | Чистая прибыль    | 4 050   | 5 100   | 4 050   | 7 725   | -11 700   | -72 675   | 20 925   | -93 600   |
      | 4:-1  | Налог             | 2 844   | 3 096   | 2 844   | 3 726   | 0         | 12 510    | 12 510   | 0         |
      | 5:-1  | Дивиденды         | 362     | 601     | 362     | 1 200   | -3 510    | -25 555   | 2 524    | -28 080   |

  Scenario: <4.13> Fill the module "Накладные расходы - Клинское"
    * Click on "Contents Element(Накладные расходы - Клинское)"
    * Check if the Grid exists * loaded
    * Check if the elements in the grid match:
      | 0:-1  | Реклама ТВ              | 750   | 800   | 750   | 925   | 0     | 0     | 0     | 0     |
      | 1:-1  | Затраты на персонал     | 600   | 600   | 600   | 600   | 600   | 600   | 600   | 600   |
      | 2:-1  | Скидки дистрибьюторам   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 3:-1  | Общие накладные затраты | 1 350 | 1 400 | 1 350 | 1 525 | 600   | 600   | 600   | 600   |
      | 4:-1  | Реклама ТВ              | 0     | 0     | 0     | 0     | 900   | 900   | 900   | 900   |
      | 5:-1  | Затраты на персонал     | 600   | 600   | 600   | 600   | 600   | 600   | 600   | 600   |
      | 6:-1  | Скидки дистрибьюторам   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 7:-1  | Общие накладные затраты | 600   | 600   | 600   | 600   | 1 500 | 1 500 | 1 500 | 1 500 |
      | 8:-1  | Реклама ТВ              | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 9:-1  | Затраты на персонал     | 600   | 600   | 600   | 600   | 600   | 600   | 600   | 600   |
      | 10:-1 | Скидки дистрибьюторам   | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 11:-1 | Общие накладные затраты | 600   | 600   | 600   | 600   | 600   | 600   | 600   | 600   |

    * Click on "Grid Cell(2:0)"
    * Type "300" into the cell at the intersection of "Jan 21" * the row number [2]
    * Check if the Grid exists * loaded
    * Type "300" into the cell at the intersection of "Feb 21" * the row number [2]
    * Check if the Grid exists * loaded
    * Type "300" into the cell at the intersection of "Mar 21" * the row number [2]
    * Check if the Grid exists * loaded
    * Type "300" into the cell at the intersection of "Apr 21" * the row number [2]
    * Check if the Grid exists * loaded
    * Type "500" into the cell at the intersection of "May 21" * the row number [6]
    * Check if the elements in the grid match:
      | 6:-1  | Скидки дистрибьюторам   |  |  |  |  | 500 |

    * Click on "Grid Cell(6:4)"
    * Click on "Button(Copy Right)"
    * Check if the elements in the grid match:
      | 6:-1  | Скидки дистрибьюторам   |  |  |  |  | 500 | 500 |

    * Check if the elements in the grid match:
      | 0:-1  | Реклама ТВ              | 750   | 800   | 750   | 925   | 0     | 0     | 0     | 0     |
      | 1:-1  | Затраты на персонал     | 600   | 600   | 600   | 600   | 600   | 600   | 600   | 600   |
      | 2:-1  | Скидки дистрибьюторам   | 300   | 300   | 300   | 300   | 0     | 0     | 0     | 0     |
      | 3:-1  | Общие накладные затраты | 1 650 | 1 700 | 1 650 | 1 825 | 600   | 600   | 600   | 600   |
      | 4:-1  | Реклама ТВ              | 0     | 0     | 0     | 0     | 900   | 900   | 900   | 900   |
      | 5:-1  | Затраты на персонал     | 600   | 600   | 600   | 600   | 600   | 600   | 600   | 600   |
      | 6:-1  | Скидки дистрибьюторам   | 0     | 0     | 0     | 0     | 500   | 500   | 500   | 500   |
      | 7:-1  | Общие накладные затраты | 600   | 600   | 600   | 600   | 2 000 | 2 000 | 2 000 | 2 000 |

  Scenario: <4.14> Control Check 3 (checking final results in "Data Input Check")
    * Click on "Contents Element(Data Input Check)"
    * Check if the elements in the grid match:
      | 0:-1  | Доходы            | 16 500  | 17 600  | 16 500  | 20 350  | 0         | 70 950    |
      | 1:-1  | Заводские расходы | 9 900   | 9 900   | 9 900   | 9 900   | 9 900     | 118 800   |
      | 2:-1  | Накладные расходы | 2 850   | 2 900   | 2 850   | 3 025   | 1 800     | 26 025    |
      | 3:-1  | Чистая прибыль    | 3 750   | 4 800   | 3 750   | 7 425   | -11 700   | -73 875   |
      | 4:-1  | Налог             | 2 772   | 3 024   | 2 772   | 3 654   | 0         | 12 222    |
      | 5:-1  | Дивиденды         | 293     | 533     | 293     | 1 131   | -3 510    | -25 829   |


  Scenario: <4.15> Fill the module "Производственные затраты"
    * Click on "Contents Element(Клин - Клинское)"
    * Check if the elements in the grid match:
      | 0:-1  | Затраты на материалы       | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 1:-1  | Затраты на изготовление    | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 2:-1  | Общезаводские затраты      | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 |
      | 3:-1  | Себестоимость производства | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 |
      | 4:-1  | Затраты на материалы       | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 5:-1  | Затраты на изготовление    | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 6:-1  | Общезаводские затраты      | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 |
      | 7:-1  | Себестоимость производства | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 |
      | 8:-1  | Затраты на материалы       | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 9:-1  | Затраты на изготовление    | 0     | 0     | 0     | 0     | 0     | 0     | 0     | 0     |
      | 10:-1 | Общезаводские затраты      | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 |
      | 11:-1 | Себестоимость производства | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 | 1 000 |


    * Click on "Grid Cell(0:0)"
    * Type "400" into the cell at the intersection of "Jan 21" * the row number [0]
    * Check if the Grid exists * loaded
    * Type "300" into the cell at the intersection of "Feb 21" * the row number [0]
    * Check if the Grid exists * loaded
    * Type "400" into the cell at the intersection of "Mar 21" * the row number [0]
    * Check if the Grid exists * loaded
    * Type "500" into the cell at the intersection of "Apr 21" * the row number [0]
    * Check if the Grid exists * loaded
    * Type "150" into the cell at the intersection of "Jan 21" * the row number [1]
    * Check if the Grid exists * loaded
    * Type "250" into the cell at the intersection of "Feb 21" * the row number [1]
    * Check if the Grid exists * loaded
    * Type "800" into the cell at the intersection of "Mar 21" * the row number [1]
    * Check if the Grid exists * loaded
    * Type "100" into the cell at the intersection of "Apr 21" * the row number [1]
    * Check if the Grid exists * loaded
    * Type "450" into the cell at the intersection of "May 21" * the row number [4]
    * Check if the elements in the grid match:
      | 4:-1  |  |  |  |  |  | 450 |

    * Click on "Grid Cell(4:4)"
    * Click on "Button(Copy Right)"
    * Check if the elements in the grid match:
      | 4:-1  |  |  |  |  |  | 450 | 450 |

    * Type "225" into the cell at the intersection of "May 21" * the row number [5]
    * Check if the elements in the grid match:
      | 5:-1  |  |  |  |  |  | 225 |

    * Click on "Grid Cell(5:4)"
    * Click on "Button(Copy Right)"
    * Check if the elements in the grid match:
      | 5:-1  |  |  |  |  |  | 225 | 225 |

    * Check if the elements in the grid match:
      | 0:-1  | Затраты на материалы       | 400   | 300   | 400   | 500   | 0       | 0       | 0       | 0       | 0       | 0       | 0       |
      | 1:-1  | Затраты на изготовление    | 150   | 250   | 800   | 100   | 0       | 0       | 0       | 0       | 0       | 0       | 0       |
      | 2:-1  | Общезаводские затраты      | 1 015 | 1 025 | 1 080 | 1 010 | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   |
      | 3:-1  | Себестоимость производства | 1 565 | 1 575 | 2 280 | 1 610 | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   |
      | 4:-1  | Затраты на материалы       |  0    | 0     | 0     | 0     | 450     | 450     | 450     | 450     | 450     | 450     | 450     |
      | 5:-1  | Затраты на изготовление    |  0    | 0     | 0     | 0     | 225     | 225     | 225     | 225     | 225     | 225     | 225     |
      | 6:-1  | Общезаводские затраты      | 1 000 | 1 000 | 1 000 | 1 000 | 1 023   | 1 023   | 1 023   | 1 023   | 1 023   | 1 023   | 1 023   |
      | 7:-1  | Себестоимость производства | 1 000 | 1 000 | 1 000 | 1 000 | 1 698   | 1 698   | 1 698   | 1 698   | 1 698   | 1 698   | 1 698   |


  Scenario: <4.16> Control Check 4 (checking final results in "Data Input Check")
    * Click on "Contents Element(Data Input Check)"
    * Check if the elements in the grid match:
      | 0:-1  | Доходы            | 16 500   | 17 600   | 16 500   | 20 350   | 0         | 70 950    |
      | 1:-1  | Заводские расходы | 10 522   | 10 533   | 11 308   | 10 571   | 9 900     | 122 133   |
      | 2:-1  | Накладные расходы | 2 910    | 3 000    | 3 170    | 3 065    | 1 800     | 26 545    |
      | 3:-1  | Чистая прибыль    | 3 068    | 4 067    | 2 022    | 6 714    | -11 700   | -77 728   |
      | 4:-1  | Налог             | 2 608    | 2 848    | 2 357    | 3 483    | 0         | 11 297    |
      | 5:-1  | Дивиденды         | 138      | 366      | -101     | 969      | -3 510    | -26 708   |
      | 6:-1  | Доходы            | 0        | 0        | 0        | 0        | 19 800    | 158 400   |
      | 7:-1  | Заводские расходы | 9 900    | 9 900    | 9 900    | 9 900    | 10 667    | 124 938   |
      | 8:-1  | Накладные расходы | 1 800    | 1 800    | 1 800    | 1 800    | 3 290     | 33 520    |
      | 9:-1  | Чистая прибыль    | -11 700  | -11 700  | -11 700  | -11 700  | 5 843     | -58       |
      | 10:-1 | Налог             | 0        | 0        | 0        | 0        | 3 274     | 26 194    |
      | 11:-1 | Дивиденды         | -3 510   | -3 510   | -3 510   | -3 510   | 771       | -7 876    |
      | 12:-1 | Доходы            | 0        | 0        | 0        | 0        | 0         | 0         |
      | 13:-1 | Заводские расходы | 9 900    | 9 900    | 9 900    | 9 900    | 9 900     | 118 800   |
      | 14:-1 | Накладные расходы | 1 800    | 1 800    | 1 800    | 1 800    | 1 800     | 21 600    |
      | 15:-1 | Чистая прибыль    | -11 700  | -11 700  | -11 700  | -11 700  | -11 700   | -140 400  |
      | 16:-1 | Налог             | 0        | 0        | 0        | 0        | 0         | 0         |
      | 17:-1 | Дивиденды         | -3 510   | -3 510   | -3 510   | -3 510   | -3 510    | -42 120   |

  Scenario: <5.1> Add subset months
    * Click on "Header Menu Element(Add Subset in Months)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Time)" in "Header Menu Element(Months)"
    * Check if "Tab Header" with text "Months" is active
    * Check if "Tab Header" with text "Subsets" is active
    * Check if the Grid exists * loaded
    * Check if "Selection Row Header(0:-1)" exists

    * Click on "Tab Header(Table)"
    * Click on "GridCell(2:2) > Checkbox"
    * Check if the Grid exists * loaded
    * Check if "GridCell(2:2) > Checkbox" is checked

    * Click on "GridCell(4:2) > Checkbox"
    * Check if the Grid exists * loaded
    * Check if "GridCell(4:2) > Checkbox" is checked

    * Click on "GridCell(10:2) > Checkbox"
    * Check if the Grid exists * loaded
    * Check if "GridCell(10:2) > Checkbox" is checked

  Scenario: <5.2> Create Dashboard * publish MK * CT
    * Click on "Header Menu Element(Add Dashboard)" in "Header Menu Element(Visualization)" in "Header Menu Element(Dashboards)"
    * Check if "Tab Header" with text "Dashboards" is active
    * Check if "Tab Header" with text "Table" is active
    * Check if the Grid exists * loaded
    * Check if "Row Header(0:-1)" exists

    * Click on "Header Menu Element(Add Context Table)" in "Header Menu Element(Visualization)" in "Header Menu Element(Context Tables)"
    * Check if "Tab Header" with text "Context Table" is active
    * Check if "Tab Header" with text "Table" is active
    * Check if the Grid exists * loaded
    * Check if "Row Header(0:-1)" exists

    * Click on "Contents Element(Доходы - Лента)"
    * Check if the Grid exists * loaded
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Publish to Dashboard)"
    * Click on "Menu Item(Dashboard #1)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist
    * Click on "Enabled Button(View)"
    * Hover over "Menu Item(Publish to Context Table)"
    * Click on "Menu Item(Context Table #1)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist

    * Click on "Contents Element(Data Input Check)"
    * Check if the Grid exists * loaded
    * Click on "Enabled Button(View)"
    * Hover over "Menu Item(Publish to Dashboard)"
    * Click on "Menu Item(Dashboard #1)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist
    * Click on "Enabled Button(View)"
    * Click on "Menu Item(Publish to Context Table)"
    * Click on "Menu Item(Context Table #1)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist

  Scenario: <5.3> Create Chart * publish to Dashboard * CT
    * Click on "Toolbar > Enabled Button(Pivot)"
    * Drag "Dnd Element(Бренды)" * drop into "Dnd Zone(Pages)"
    * Check if "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    * Drag "Dnd Element(Versions)" * drop into "Dnd Zone(Pages)"
    * Check if "Dnd Zone(Pages) > Dnd Element(Versions)" exists
    * Click on "Modal > Button(Ok)"
    * Check if the Grid exists * loaded
    * Click on "Upper Left Cell"
    * Click on "Toolbar > Enabled Button(Charts)"
    * Click on "Menu Item(Combination Chart)"
    * Wait until the modal form is open
    * Check if "Any Loader" does not exist
    * Click on "Modal > Checkbox(Omit Summary Rows)"
    * Click on "Modal > Checkbox(Omit summary columns)"
    * Click on "Modal > Checkbox(Omit empty values)"
    * Click on "Modal > Checkbox(Show Bar Labels)"
    * Check if "Modal > Checkbox(Show Bar Labels)" is checked

    * Click on "Modal > Button(View)"
    * Hover over "Menu Item(Publish to Dashboard)"
    * Click on "Menu Item(Dashboard #1)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist
    * Click on "Modal > Button(View)"
    * Click on "Menu Item(Publish to Context Table)"
    * Click on "Menu Item(Context Table #1)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist
    * Click on "Modal > Icon(close)"
    * Check if "Modal" does not exist
    * Check if the Grid exists * loaded

  Scenario: <5.4> Edit Settings cards on DB
    * Click on "Contents Element(Dashboard #1)"
    * Check if "Any Loader" does not exist
    * Check if "Card Of Dashboards(Доходы - Лента)" exists
    * Check if "Card Of Dashboards(Data Input Check)" exists
    * Check if "Card Of Dashboards(Chart Фин. результат)" exists

    * Check if "Tab Header" with text "Edit Mode" is not active
    * Click on "Tab Header(Edit Mode)"
    * Check if "Tab Header" with text "Edit Mode" is active
    * Check if "Any Loader" does not exist
    * Hover over "Card Of Dashboards(Доходы - Лента)"
    * Check if "Card Of Dashboards(Доходы - Лента) > Button(Card Settings)" exists
    * Click on "Card Of Dashboards(Доходы - Лента) > Enabled Button(Card Settings)"
    * Check if "Modal" exists

    * Click on "Advanced Tab Card Setting"
    * Type "22" into "Input(w)"
    * Check if "Modal > Input(w)" attribute value equals to "22"
    * Click on "Modal > Enabled Button(Apply)"
    * Check if "Modal" does not exist
    * Check if "Any Loader" does not exist

    * Hover over "Card Of Dashboards(Data Input Check)"
    * Check if "Card Of Dashboards(Data Input Check) > Button(Card Settings)" exists
    * Click on "Card Of Dashboards(Data Input Check) > Enabled Button(Card Settings)"
    * Check if "Modal" exists
    * Click on "Advanced Tab Card Setting"
    * Type "22" into "Input(w)"
    * Check if "Modal > Input(w)" attribute value equals to "22"
    * Click on "Modal > Enabled Button(Apply)"
    * Check if "Modal" does not exist
    * Check if "Any Loader" does not exist

    * Click on "Dashboard Toolbar > Button(Apply)"  
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist
    * Click on "Tab Header(Dashboard #1)"
    * Check if "Tab Header" with text "Edit Mode" is not active
    * Check if "Any Loader" does not exist
    * Check if "Card Of Dashboards(Доходы - Лента)" exists
    * Check if "Card Of Dashboards(Data Input Check)" exists

  Scenario: <5.5> Filtration card via Subset Filter
    * Right click on "Card Of Dashboards(Доходы - Лента) > Col Header(-1:0)"
    * Click on "Menu Item(Subset Filter)"
    * Check if "Modal" exists
    * Check if "Modal" contains "Subset Filter"
    * Check if "Tab Header" with text "View Mode" is active
    * Check if "Modal > Input(subset)" attribute value equals to "None"
    * Click on "Dropdown(subset)"
    * Check if "Dropdown(subset) > Dropdown Option(Time Subset #19)" exists
    * Click on "Dropdown(subset) > Dropdown Option(Time Subset #19)"
    * Check if "Modal > Input(subset)" attribute value equals to "Time Subset #19"

    * Click on "Modal > Button(Ok)"
    * Check if "Modal" does not exist
    * Check if "Any Loader" does not exist
    * Check if "Card Of Dashboards(Доходы - Лента) > Col Header(-1:0|Mar 21)" exists
    * Check if "Card Of Dashboards(Доходы - Лента) > Col Header(-1:1|May 21)" exists
    * Check if "Card Of Dashboards(Доходы - Лента) > Col Header(-1:2|Nov 21)" exists
    * Check if "Card Of Dashboards(Доходы - Лента) > Col Header(-1:3|FY21)" exists
    * Check if "Card Of Dashboards(Доходы - Лента) > Col Header(-1:4|YTD)" exists
    * Check if "Card Of Dashboards(Доходы - Лента) > Col Header(-1:5|YTG)" exists
    * Check if "Card Of Dashboards(Доходы - Лента) > Col Header(-1:6)" does not exist

    * Hover over "Card Of Dashboards(Доходы - Лента) > SwitchToolbar"
    * Check if "Card Of Dashboards(Доходы - Лента) > Button(Save)" exists
    * Click on "Card Of Dashboards(Доходы - Лента) > Enabled Button(Save)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist

  Scenario: <5.6> Сonfigure the context between cards
    * Click on "Tab Header(Edit Mode)"
    * Check if "Tab Header" with text "Edit Mode" is active
    * Check if "Any Loader" does not exist
    * Hover over "Card Of Dashboards(Data Input Check)"
    * Check if "Card Of Dashboards(Data Input Check) > Button(Card Settings)" exists
    * Click on "Card Of Dashboards(Data Input Check) > Enabled Button(Card Settings)"
    * Wait until the modal form is open
    * Check if "Modal" exists
    * Click on "Modal > Tab Header(Basic)"
    * Check if "Modal > Tab Header(Basic)" is active
    * Click on "Modal > Checkbox(Dependent Context)"
    * Check if "Modal > Checkbox(Dependent Context)" is checked
    * Check if "Modal > Input(dependOn)" attribute value equals to ""
    * Select element "Доходы - Лента" in "Dropdown(dependOn)"
    * Check if "Modal > Input(dependOn)" attribute value equals to "Доходы - Лента"
    * Click on "Modal > Enabled Button(Apply)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist

    * Scroll the "vertical" "Dashboard Scroll Content" by [700] pixels
    * Hover over "Card Of Dashboards(Chart Фин. результат)"
    * Check if "Card Of Dashboards(Chart Фин. результат) > Button(Card Settings)" exists
    * Click on "Card Of Dashboards(Chart Фин. результат) > Enabled Button(Card Settings)"
    * Check if "Modal" exists
    * Click on "Modal > Tab Header(Basic)"
    * Click on "Modal > Checkbox(Dependent Context)"
    * Check if "Modal > Checkbox(Dependent Context)" is checked
    * Check if "Modal > Input(dependOn)" attribute value equals to ""
    * Select element "Доходы - Лента" in "Dropdown(dependOn)"
    * Check if "Modal > Input(dependOn)" attribute value equals to "Доходы - Лента"
    * Click on "Modal > Enabled Button(Apply)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist

    * Click on "Dashboard Toolbar > Button(Apply)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist
    * Click on "Tab Header(Dashboard #1)"
    * Check if "Tab Header" with text "Edit Mode" is not active
    * Check if "Any Loader" does not exist
    * Check if "Card Of Dashboards(Доходы - Лента)" exists
    * Check if "Card Of Dashboards(Data Input Check)" exists
    
  Scenario: <5.7> Apply dependent context via column header for child cards
    * Scroll the "vertical" "Dashboard Scroll Content" by [0] pixels
    * Check if the elements in context "Card of Dashboards(Доходы - Лента)" grid match:
     | 0:-1  | Total Br*s | 15 000 | 0 | 0 | 64 500 | 64 500 | 0 |
     | 1:-1  | Клинское     | 15 000 | 0 | 0 | 64 500 | 64 500 | 0 |

    * Check if the elements in context "Card of Dashboards(Data Input Check)" grid match:
     | 0:-1  | Доходы            | 16 500   | 17 600   | 16 500   | 20 350   | 0         | 70 950    |
     | 1:-1  | Заводские расходы | 10 522   | 10 533   | 11 308   | 10 571   | 9 900     | 122 133   |

    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:0|Jan 21)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:1|Feb 21)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:2|Mar 21)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:5|FY21)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:6|YTD)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:7|YTG)" exists
    * Check if "Card Of Dashboards(Chart Фин. результат) > Filter(Total Br*s)" exists
    * Check if "Card Of Dashboards(Chart Фин. результат) > Filter(Previous Plan)" exists

    * Click on "Card Of Dashboards(Доходы - Лента) > Col Header(-1:1|May 21)"
    * Check if "Any Loader" does not exist
    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:0|May 21)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:1|FY21)" exists
    * Check if "Card Of Dashboards(Chart Фин. результат) > Filter(Total Br*s)" exists
    * Check if "Card Of Dashboards(Chart Фин. результат) > Filter(Previous Plan)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Col Header(-1:2)" does not exist
    * Check if the elements in context "Card of Dashboards(Data Input Check)" grid match:
     | 0:-1  | Доходы            | 0     | 70 950  |
     | 1:-1  | Заводские расходы | 9 900 | 122 133 |

  Scenario: <5.8> Filtration card via Select level to show
    * Check if "Card Of Dashboards(Data Input Check) > Row Header(0:-2, Total Br*s)" exists
    * Right click on "Card Of Dashboards(Data Input Check) > Row Header(0:-2)"
    * Check if "Grid Context Menu" was opened
    * Click on "Menu Item(Reselect Level)"
    * Wait until the modal form is open
    * Check if "Modal > Checkbox(summaries)" is checked
    * Check if "Modal > Checkbox(details)" is not checked
    * Click on "Modal > Checkbox(details)"
    * Click on "Modal > Checkbox(summaries)"
    * Check if "Modal > Checkbox(details)" is checked
    * Check if "Modal > Checkbox(summaries)" is not checked
    * Click on "Modal > Button(Ok)"
    * Check if "Any Loader" does not exist
    * Check if "Card Of Dashboards(Data Input Check) > Row Header(0:-2, Клинское)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Row Header(6:-2, Толстяк)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Row Header(12:-2, Балтика)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Row Header(18:-2, Клинское)" exists

  Scenario: <5.9> Dependent context via list dimensions for child card * chart
    * Click on "Card Of Dashboards(Доходы - Лента) > Row Header(2:-1, Толстяк)"
    * Check if "Any Loader" does not exist
    * Check if "Card Of Dashboards(Data Input Check) > Row Header(0:-2, Толстяк)" exists
    * Check if "Card Of Dashboards(Data Input Check) > Row Header(Клинское)" does not exist
    * Check if "Card Of Dashboards(Data Input Check) > Row Header(Балтика)" does not exist
    * Check if the elements in context "Card of Dashboards(Data Input Check)" grid match:
      | 0:-1  | Доходы            | 0     | 0     | 0     | 0     | 0     | 0      |
      | 1:-1  | Заводские расходы | 3 300 | 3 300 | 3 300 | 3 300 | 3 300 | 39 600 |

    * Check if "Card Of Dashboards(Chart Фин. результат) > Filter(Толстяк)" exists
    * Check if "Card Of Dashboards(Chart Фин. результат) > Filter(Previous Plan)" exists

  Scenario: <5.10> Settings for CT
    * Click on "Contents Element(Context Table #1)"
    * Check if the Grid exists * loaded
    * Check if "Tab Header" with text "Context Table #1" is active
    * Click on "Tab Header(Data Input Check)"
    * Check if "Tab Header" with text "Data Input Check" is active
    * Check if the Grid exists * loaded
    * Click on "Toolbar > Enabled Button(Conditional Formatting)"
    * Check if "Modal" exists
    * Click on "Modal > Button(New Rule)"
    * Check if "Modal" contains "New Rule"
    * Select element "Накладные расходы" in "Dropdown(currentLongId)"
    * Select element "Доходы" in "Dropdown(dependLongId)"

    * Select element "3-color scale" in "Dropdown(typeColorSchema)"
    * Type "17000" into "Conditional Formatting(Mid-point) > Input"
    * Type "20000" into "Conditional Formatting(Maximum) > Input"
    * Check if "Button(Ok)" is not disabled
    * Click on "Modal > Button(Ok)"
    * Check if "Modal" contains "Manage Conditional Formatting"
    * Check if "Modal > Conditional Formatting Element(Накладные расходы)" exists
    * Click on "Modal > Button(Apply)"
    * Check if the Grid exists * loaded
    * Check if "Modal" does not exist

  Scenario: <5.11> Add Model Filter
    * Click on "Contents > Button(Toolbar Settings)"
    * Check if "Modal" exists
    * Check if "Dnd Zone(Off) > Dnd Element(Version)" exists
    * Drag "Dnd Zone(Off) > Dnd Element(Version)" * drop into "Dnd Zone(On)"
    * Check if "Dnd Zone(On) > Dnd Element(Version)" exists
    * Check if "Modal > Filter(Previous Plan)" exists
    * Change the filter from "Previous Plan" to "Actual"
    * Check if "Modal > Filter(Actual)" exists
    * Click on "Modal > Button(Apply)"
    * Check if "Any Loader" does not exist
    * Check if "Contents > Filter(Actual)" exists

  Scenario: <5.12> Add context via Model Filter on tab CT
    * Click on "ToolbarRightSide > Button(settings)"
    * Check if "Modal" exists
    * Click on "Modal > Checkbox(Dependent Context)"
    * Check if "Modal > Checkbox(Dependent Context)" is checked

    * Select element "Model Filter: Versions" in "Dropdown(dependOn)"
    * Check if "Modal > Input(dependOn)" attribute value equals to "Model Filter: Versions"
    * Click on "Modal > Enabled Button(Apply)"
    * Check if "Any Loader" exists
    * Check if "Any Loader" does not exist
    * Check if "Row Header(0:-3, Actual)" exists
    * Check if "Row Header(0:-1)" exists
    * Check if "Row Header(6:-3)" does not exist
    * Check if "Row Header(6:-1)" does not exist

    * Click on "Contents > Filter(Actual)"
    * Check if "Tree Menu Element(Current Plan)" exists
    * Click on text "Current Plan" in "Tree Menu Element"
    * Check if "Contents > Filter(Current Plan)" exists
    * Check if "Any Loader" does not exist
    * Check if "Row Header(0:-3, Current Plan)" exists

  Scenario: <5.10> Revert model
    * Click on "Header Menu Element(Logs)" in "Header Menu Element(Security Center)"
    * Check if the Grid exists * loaded
    * Check if "Row Header(2, 0:-1)" exists
    * Check if "Row Header(1, 1:-1)" exists

    * Click on "Row Header(1:-1)"
    * Click on "Button(Restore)"
    * Click on "Modal > Input"
    * Type "1"
    * Click on "Modal > Button(Restore)"
    * Check if "Global Loader" exists
    * Check if "Global Loader" does not exist
    * Check if the Grid exists * loaded
    * Check if "Row Header(1, 0:-1)" exists
    * Check if "Row Header(2)" does not exist

   # Scenario: <Service>  I destroy environment
    # * Delete the current model
```


[Оглавление](../README.md)
