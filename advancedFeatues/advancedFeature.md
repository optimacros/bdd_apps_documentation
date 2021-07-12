# SPD Тест - Sales Presentation Demo

Этот тест подготавливает модель к работе моделлера.

Строится нужное время, версии, справочники и их зависимости. Следом на основе построенных измерений создаются Мультикубы с определенной структурой и расположением измерений на нужных плоскостях (строки, колонки или фильтра)

Так же вбиваются нужные формулы мультикубов, меняются данные и сравниваются финальные данные грида. 

Тест выполяется в неизолированной модели с созданием бекапа, в конце тест возвращает модель в исходное состояние до запуска теста.

Если требуется построить модель и использовать ее далее, то нужно удалить шаги с ``Restore`` модели, а в начале можно указать чтоб тест запускался в изолированном виде!

```JS
@thread11
Feature: UI - Builder Menu - Dimensions - Time - Tabs

  Scenario: <Service> I prepare environment
    Given Not isolated "E2E SPD" model
    Given App as "modeller"

  Scenario: <1.1> Choose Current Period as Apr 21
    When I call the manual backup with hot keys
    And I see that "Notification(Start backup model)" exists
    And I see that "Notification(Start backup model)" doesn't exist
    And I see that "Notification(Your backup was saved successfully)" exists
    Then I see that "Notification(Your backup was saved successfully)" doesn't exist

    When I click on "Header Menu Element(Logs)" in "Header Menu Element(Security Center)"
    And I see that Grid exists and loaded
    Then I see that "Row Header(2, 0:-1)" exists

    When I click on "Header Menu Element(Time)" in "Header Menu Element(Dimensions)"
    And I see that Grid exists and loaded
    And I click on "Grid Cell(5:0)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Filter Element(Apr 21)" exists
    And I click on "Filter Element(Apr 21)"
    Then I see elements in the grid:
      | 5:-1 | Current Month  |  Apr 21 |

  Scenario: <1.2> Confirm selection of Current Detail Period
    When I click on "Header Menu Element(Time)" in "Header Menu Element(Dimensions)"
    And I click on "Toolbar > Button(Apply)"
    And I wait until modal is opened
    And I click on "Button(Ok)"
    Then I see that "Button(Apply)" is disabled


  Scenario: <1.3> Create new version at the end of the list
    When I click on "Header Menu Element(Versions)" in "Header Menu Element(Dimensions)"
    And I see that Grid exists and loaded
    And I insert "Versions" elements at the "Start":
      """
      Previous Plan
      """

    Then I see elements in the grid:
      | 0:-1 | Previous Plan |        |
      | 1:-1 | Actual        |        |
      | 2:-1 | Forecast      | Actual |


  Scenario: <1.4> Rename "Forecast" to "Current Plan"
    When I click on "Row Header(Forecast)"
    And I type "Current Plan"
    And I press "ENTER"
    Then I see elements in the grid:
      | 0:-1 | Previous Plan |
      | 1:-1 | Actual        |
      | 2:-1 | Current Plan  |


  Scenario: <1.5> Set SwitchOver of the "Current Plan" onto "May 21"
    And I click on "Grid Cell(2:1)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Tree Menu" exists
    And I type "1 May 21"
    And I click on "Filter Element(1 May 21)"
    Then I see elements in the grid:
      | 0:-1 | Previous Plan |        |          |
      | 1:-1 | Actual        |        |          |
      | 2:-1 | Current Plan  | Actual | 1 May 21 |


  Scenario: <1.6> Insert "Бренды" into Lists
    When I click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"
    And I insert "Lists" elements at the "Start":
      """
    Бренды
      """

    Then I see elements in the grid:
      | 0:-1 | Бренды |


  Scenario: <1.7> Insert data to the "Бренды"
    When I click on "Header Menu Element(Бренды)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
    And I insert "Elements" elements at the "Start":
      """
      Клинское
      Толстяк
      Балтика
      """

    Then I see elements in the grid:
      | 0:-1 | Клинское |
      | 1:-1 | Толстяк  |
      | 2:-1 | Балтика  |


  Scenario: <1.8> Define the Top Level for "Бренды"
    When I click on "Tab Header(Settings)"
    And I type "Total Brands" into property "Бренды" of element "Top Level"
    And I click on "Tab Header(Table)"

    Then I see elements in the grid:
      | 0:-1 | Total Brands |
      | 1:-1 | Клинское     |
      | 2:-1 | Толстяк      |
      | 3:-1 | Балтика      |

  Scenario: <1.9> Add more hierarchies into "Lists"
    When I click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"
    And I insert "Lists" elements at the "End":
      """
      Заводы
      Материалы
      2.1 Регионы
      2.2 Клиенты
      """

    Then I see elements in the grid:
      | 0:-1 | Бренды      | Total Brands |
      | 1:-1 | Заводы      |              |
      | 2:-1 | Материалы   |              |
      | 3:-1 | 2.1 Регионы |              |
      | 4:-1 | 2.2 Клиенты |              |


  Scenario: <1.10> Set up the "Заводы" hierarchy
    When I click on "Header Menu Element(Заводы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"

    And I insert "Elements" elements at the "Start":
      """
      Клин
      Курск
      Иваново
      """

    When I click on "Tab Header(Settings)"
    And I type "Total Factories" into property "Заводы" of element "Top Level"
    And I click on "Tab Header(Table)"
    Then I see elements in the grid:
      | 0:-1 | Total Factories |
      | 1:-1 | Клин            |
      | 2:-1 | Курск           |
      | 3:-1 | Иваново         |


  Scenario: <1.11> Set up the "Материалы" hierarchy
    When I click on "Header Menu Element(Материалы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
    And I insert "Elements" elements at the "Start":
      """
      Хмель
      Солод
      Вода
      Соль
      """

    When I click on "Tab Header(Settings)"
    And I type "Total Materials" into property "Материалы" of element "Top Level"
    And I click on "Tab Header(Table)"
    Then I see elements in the grid:
      | 0:-1 | Total Materials |
      | 1:-1 | Хмель           |
      | 2:-1 | Солод           |
      | 3:-1 | Вода            |
      | 4:-1 | Соль            |


  Scenario: <1.12> Set up the "2.1 Регионы" hierarchy
    When I click on "Header Menu Element(2.1 Регионы)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
    And I insert "Elements" elements at the "Start":
      """
      Запад
      Центр
      Юг
      Восток
      """

    When I click on "Tab Header(Settings)"
    And I type "Total Company" into property "2.1 Регионы" of element "Top Level"
    And I click on "Tab Header(Table)"

    Then I see elements in the grid:
      | 0:-1 | Total Company |
      | 1:-1 | Запад         |
      | 2:-1 | Центр         |
      | 3:-1 | Юг            |
      | 4:-1 | Восток        |


  Scenario: <1.13> Set up the "2.2 Клиенты" hierarchy
    When I click on "Header Menu Element(2.2 Клиенты)" in "Header Menu Element(Dimensions)" in "Header Menu Element(Lists)"
    And I insert "Elements" elements at the "Start":
      """
      Лента
      Карусель
      Азбука Вкуса
      Перекресток
      Магнит
      Красное и Белое
      """

    Then I see elements in the grid:
      | 0:-1 | Лента           |
      | 1:-1 | Карусель        |
      | 2:-1 | Азбука Вкуса    |
      | 3:-1 | Перекресток     |
      | 4:-1 | Магнит          |
      | 5:-1 | Красное и Белое |


  Scenario: <1.14> Set parent hierarchy for "2.2 Клиенты"
    When I click on "Tab Header(Settings)"
    And I click on "Grid Cell(1:0)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Tree Menu" exists
    And I click on "Filter Element(2.1 Регионы)"
    And I click on "Tab Header(Table)"
    Then I see elements in the grid:
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
    When I click on "Grid Cell(5:2)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Tree Menu" exists
    Then I click on "Filter Element(Запад)"

    When I click on "Grid Cell(6:2)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Tree Menu" exists
    Then I click on "Filter Element(Запад)"

    When I click on "Grid Cell(7:2)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Tree Menu" exists
    Then I click on "Filter Element(Центр)"

    When I click on "Grid Cell(8:2)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Tree Menu" exists
    Then I click on "Filter Element(Центр)"

    When I click on "Grid Cell(9:2)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Tree Menu" exists
    Then I click on "Filter Element(Юг)"

    When I click on "Grid Cell(10:2)"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Tree Menu" exists
    Then I click on "Filter Element(Восток)"


    Then I see elements in the grid:
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
    When I click on "Header Menu Element(Lists)" in "Header Menu Element(Dimensions)"

    Then I see elements in the grid:
      | 0:-1 | Бренды      | Total Brands    |             |
      | 1:-1 | Заводы      | Total Factories |             |
      | 2:-1 | Материалы   | Total Materials |             |
      | 3:-1 | 2.1 Регионы | Total Company   |             |
      | 4:-1 | 2.2 Клиенты |                 | 2.1 Регионы |


  Scenario: <1.17> Create "Functional Areas"
    When I click on "Header Menu Element(Folders)" in "Header Menu Element(Visualization)"
    And I insert "Folders" elements at the "Start":
      """
      Доходы и Расходы
      Финансовый Результат
      """

    Then I see elements in the grid:
      | 0:-1 | Доходы и Расходы     |
      | 1:-1 | Финансовый Результат |


  Scenario: <2.1> Create module "Доходы"
    When I click on "Header Menu Element(Multicubes)" in "Header Menu Element(Data)"
    And I click on "Enabled Button(Add Multicube with Name)"
    And I click on "Modal > Button(Place)"
    And I drag "Dnd Zone(Available) > Dnd Element(Versions)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Versions)" exists
    And I drag "Dnd Zone(Available) > Dnd Element(Бренды)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Бренды)" exists
    And I drag "Dnd Zone(Available) > Dnd Element(2.2 Клиенты)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(2.2 Клиенты)" exists

    And I type into "Input(Line Items)":
      """
      Продажи
      Upsale
      """

    And I click on "Modal > Tab Header(Advanced)"
    And I type "Доходы" into "Input(New Powercube Name)"
    And I select option "Доходы и Расходы" in "Dropdown(categories)"
    And I see "Modal > Input(categories)" with attribute value equal "Доходы и Расходы"
    And I click on "Button(Create)"
    Then I see elements in the grid:
      | 0:-1 | Продажи |
      | 1:-1 | Upsale  |


  Scenario: <2.2> Insert a Line Item using the Edit Mode
    When I click on "Tab Header(Edit Mode)"
    And I insert "Cubes" elements at the "End":
      """
      Общие доходы
      """

    Then I see elements in the grid:
      | 0:-1 | Доходы          |
      | 1:-1 |   Продажи       |
      | 2:-1 |   Upsale        |
      | 3:-1 |   Общие доходы  |


  Scenario: <2.3> Check the module structure
    When I click on "Tab Header(Доходы)"
    Then I see elements in the grid:
      | 0:-1 | Продажи       | 0 | 0 | 0 | 0 | 0 | 0 |
      | 1:-1 | Upsale        | 0 | 0 | 0 | 0 | 0 | 0 |
      | 2:-1 | Общие доходы  | 0 | 0 | 0 | 0 | 0 | 0 |

    And I click on "Tab Header(Доходы) > Icon(close)"

  Scenario: <2.4> Create module "Производственные затраты"
    When I click on "Header Menu Element(Add Multicube)" in "Header Menu Element(Data)" in "Header Menu Element(Multicubes)"
    And I see that "Modal" exists
    And I click on "Modal > Button(Place)"
    And I drag "Dnd Zone(Available) > Dnd Element(Versions)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Versions)" exists
    And I drag "Dnd Zone(Available) > Dnd Element(Бренды)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Бренды)" exists
    And I drag "Dnd Zone(Available) > Dnd Element(Заводы)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Заводы)" exists
    And I type into "Input(Line Items)":
      """
      Затраты на материалы
      Затраты на изготовление
      Общезаводские затраты
      Себестоимость производства
      """

    And I click on "Modal > Tab Header(Advanced)"
    And I type "Производственные затраты" into "Input(New Powercube Name)"
    And I select option "Доходы и Расходы" in "Dropdown(categories)"
    And I see "Modal > Input(categories)" with attribute value equal "Доходы и Расходы"
    And I click on "Button(Create)"
    Then I see elements in the grid:
      | 0:-1 | Затраты на материалы       |
      | 1:-1 | Затраты на изготовление    |
      | 2:-1 | Общезаводские затраты      |
      | 3:-1 | Себестоимость производства |

    And I click on "Tab Header(Производственные затраты) > Icon(close)"


  Scenario: <2.5> Create module "Накладные расходы"
    When I click on "Header Menu Element(Add Multicube)" in "Header Menu Element(Data)" in "Header Menu Element(Multicubes)"
    And I see that "Modal" exists
    And I click on "Modal > Button(Place)"
    And I drag "Dnd Zone(Available) > Dnd Element(Versions)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Versions)" exists
    And I drag "Dnd Zone(Available) > Dnd Element(Бренды)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Бренды)" exists
    And I type into "Input(Line Items)":
      """
      Реклама ТВ
      Затраты на персонал
      Скидки дистрибьюторам
      Общие накладные затраты
      """

    And I click on "Modal > Tab Header(Advanced)"
    And I type "Накладные расходы" into "Input(New Powercube Name)"
    And I select option "Доходы и Расходы" in "Dropdown(categories)"
    And I see "Modal > Input(categories)" with attribute value equal "Доходы и Расходы"
    And I click on "Button(Create)"
    Then I see elements in the grid:
      | 0:-1 | Реклама ТВ              |
      | 1:-1 | Затраты на персонал     |
      | 2:-1 | Скидки дистрибьюторам   |
      | 3:-1 | Общие накладные затраты |

    And I click on "Tab Header(Накладные расходы) > Icon(close)"


  Scenario: <2.6> Create module "Фин. результат"
    When I click on "Header Menu Element(Add Multicube)" in "Header Menu Element(Data)" in "Header Menu Element(Multicubes)"
    And I see that "Modal" exists
    And I click on "Modal > Button(Place)"
    And I drag "Dnd Zone(Available) > Dnd Element(Versions)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Versions)" exists
    And I drag "Dnd Zone(Available) > Dnd Element(Бренды)" and drop it after "Dnd Element(Filters)"
    And I see that "Dnd Zone(Selected) > Dnd Element(Бренды)" exists
    And I type into "Input(Line Items)":
      """
      Доходы
      Заводские расходы
      Накладные расходы
      Чистая прибыль
      Налог
      Дивиденды
      """

    And I click on "Modal > Tab Header(Advanced)"
    And I type "Фин. результат" into "Input(New Powercube Name)"
    And I click on "Button(Create)"
    Then I see elements in the grid:
      | 0:-1 | Доходы            |
      | 1:-1 | Заводские расходы |
      | 2:-1 | Накладные расходы |
      | 3:-1 | Чистая прибыль    |
      | 4:-1 | Налог             |
      | 5:-1 | Дивиденды         |

    Then I click on "Tab Header(Фин. результат) > Icon(close)"

  Scenario: <3.1> Change view for "Доходы"
    When I click on "Contents Element(Доходы)"
    And I see that Grid exists and loaded
    And I click on "Toolbar > Enabled Button(Pivot)"

    And I drag "Dnd Element(Versions)" and drop it after "Dnd Element(Cubes)"
    And I see that "Dnd Zone(Rows) > Dnd Element(Versions)" exists
    And I drag "Dnd Element(2.2 Клиенты)" and drop it into "Dnd Zone(Pages)"
    And I see that "Dnd Zone(Pages) > Dnd Element(2.2 Клиенты)" exists
    And I drag "Dnd Element(Бренды)" and drop it into "Dnd Zone(Pages)"
    And I see that "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    And I click on "Button(Ok)"

    Then I see elements in the grid:
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
    When I click on "Enabled Button(View)"
    And I click on "Menu Item(Save)"
    And I see that "Modal" exists
    And I click on "Modal > Button(Ok)"
    Then I see that "Modal" doesn't exist

    When I reload app
    And I see that "Global Loader" exists
    And I see that "Tab Header" with text "Доходы" is active
    And I see that "Any Loader" doesn't exist
    Then I see that "Filter(Total Company)" exists
    Then I see elements in the grid:
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
    When I click on "Toolbar > Enabled Button(Pivot)"
    And I drag "Dnd Element(Бренды)" and drop it into "Dnd Zone(Rows)"
    And I see that "Dnd Zone(Rows) > Dnd Element(Бренды)" exists
    And I click on "Button(Ok)"
    And I see that "Filter(Total Company)" exists
    Then I see elements in the grid:
      | 0:-1  | Total Brands | 0 | 0 |
      | 1:-1  |   Клинское   | 0 | 0 |
      | 2:-1  |   Толстяк    | 0 | 0 |
      | 3:-1  |   Балтика    | 0 | 0 |
      | 4:-1  | Total Brands | 0 | 0 |
      | 5:-1  |   Клинское   | 0 | 0 |
      | 6:-1  |   Толстяк    | 0 | 0 |
      | 7:-1  |   Балтика    | 0 | 0 |

  Scenario: <3.4> "Save As..." the view "Доходы - Лента"
    When I click on "Enabled Button(View)"
    And I click on "Menu Item(Save As)"
    And I see that "Modal" exists
    And I type "Доходы - Лента" into "Input(New View Name)"
    And I see that "Modal > Radio Button(New)" is checked
    And I see that "Modal > Checkbox(Model Global View)" is checked
    And I click on "Button(Ok)"
    Then I see that "Contents Element(Доходы - Лента)" exists

    When I reload app
    And I see that "Global Loader" exists
    And I see that "Tab Header" with text "Доходы - Лента" is active
    And I see that "Any Loader" doesn't exist
    Then I see that "Filter(Total Company)" exists

  Scenario: <3.5> Change view for "Накладные расходы"
    When I click on "Contents Element(Накладные расходы)"
    And I see that Grid exists and loaded
    And I click on "Enabled Button(Pivot)"
    And I drag "Dnd Element(Versions)" and drop it before "Dnd Element(Cubes)"
    And I see that "Dnd Zone(Rows) > Dnd Element(Versions)" exists
    And I drag "Dnd Element(Бренды)" and drop it into "Dnd Zone(Pages)"
    And I see that "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    And I click on "Button(Ok)"
    Then I see elements in the grid:
      | 0:-1  | Реклама ТВ              | 0 | 0 |
      | 1:-1  | Затраты на персонал     | 0 | 0 |
      | 2:-1  | Скидки дистрибьюторам   | 0 | 0 |
      | 3:-1  | Общие накладные затраты | 0 | 0 |
      | 4:-1  | Реклама ТВ              | 0 | 0 |
      | 5:-1  | Затраты на персонал     | 0 | 0 |
      | 6:-1  | Скидки дистрибьюторам   | 0 | 0 |
      | 7:-1  | Общие накладные затраты | 0 | 0 |

  Scenario: <3.6> Save current view as default view for "Накладные расходы"
    When I click on "Enabled Button(View)"
    And I click on "Menu Item(Save)"
    And I see that "Modal" exists
    And I click on "Modal > Button(Ok)"
    Then I see that "Modal" doesn't exist
    And I click on "Tab Header(Накладные расходы) > Icon(close)"

    And I click on "Contents Element(Накладные расходы)"
    And I see that "Filter(Total Brands)" exists
    Then I see elements in the grid:
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
    When I change filter "Total Brands" to "Клинское"
    Then I see elements in the grid:
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
    When I click on "Enabled Button(View)"
    And I click on "Menu Item(Save As)"
    And I see that "Modal" exists
    And I type "Накладные расходы - Клинское" into "Input(New View Name)"
    And I see that "Modal > Radio Button(New)" is checked
    And I see that "Modal > Checkbox(Model Global View)" is checked
    And I click on "Button(Ok)"
    Then I see that "Contents Element(Накладные расходы - Клинское)" exists
    And I click on "Tab Header(Накладные расходы - Клинское) > Icon(close)"


  Scenario: <3.9> Change view for "Производственные затраты"
    When I click on "Contents Element(Производственные затраты)"
    And I see that Grid exists and loaded
    And I click on "Enabled Button(Pivot)"
    And I drag "Dnd Element(Versions)" and drop it before "Dnd Element(Cubes)"
    And I see that "Dnd Zone(Rows) > Dnd Element(Versions)" exists
    And I drag "Dnd Element(Заводы)" and drop it into "Dnd Zone(Pages)"
    And I see that "Dnd Zone(Pages) > Dnd Element(Заводы)" exists
    And I drag "Dnd Element(Бренды)" and drop it into "Dnd Zone(Pages)"
    And I see that "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    And I click on "Button(Ok)"
    Then I see elements in the grid:
      | 0:-1  | Затраты на материалы       | 0 | 0 |
      | 1:-1  | Затраты на изготовление    | 0 | 0 |
      | 2:-1  | Общезаводские затраты      | 0 | 0 |
      | 3:-1  | Себестоимость производства | 0 | 0 |
      | 4:-1  | Затраты на материалы       | 0 | 0 |
      | 5:-1  | Затраты на изготовление    | 0 | 0 |
      | 6:-1  | Общезаводские затраты      | 0 | 0 |
      | 7:-1  | Себестоимость производства | 0 | 0 |


  Scenario: <3.10> Save current view as default view for "Производственные затраты"
    When I click on "Enabled Button(View)"
    And I click on "Menu Item(Save)"
    And I see that "Modal" exists
    And I click on "Modal > Button(Ok)"
    Then I see that "Modal" doesn't exist
    And I click on "Tab Header(Производственные затраты) > Icon(close)"
    And I click on "Contents Element(Производственные затраты)"
    Then I see that "Filter(Total Factories)" exists
    Then I see elements in the grid:
      | 0:-1  | Затраты на материалы       | 0 | 0 |
      | 1:-1  | Затраты на изготовление    | 0 | 0 |
      | 2:-1  | Общезаводские затраты      | 0 | 0 |
      | 3:-1  | Себестоимость производства | 0 | 0 |
      | 4:-1  | Затраты на материалы       | 0 | 0 |
      | 5:-1  | Затраты на изготовление    | 0 | 0 |
      | 6:-1  | Общезаводские затраты      | 0 | 0 |
      | 7:-1  | Себестоимость производства | 0 | 0 |


  Scenario: <3.11> Create "Клин - Клинское" view
    When I change filter "Total Factories" to "Клин"
    And I change filter "Total Brands" to "Клинское"
    Then I see elements in the grid:
      | 0:-1  | Затраты на материалы       | 0 | 0 |
      | 1:-1  | Затраты на изготовление    | 0 | 0 |
      | 2:-1  | Общезаводские затраты      | 0 | 0 |
      | 3:-1  | Себестоимость производства | 0 | 0 |
      | 4:-1  | Затраты на материалы       | 0 | 0 |
      | 5:-1  | Затраты на изготовление    | 0 | 0 |
      | 6:-1  | Общезаводские затраты      | 0 | 0 |
      | 7:-1  | Себестоимость производства | 0 | 0 |


  Scenario: <3.12> "Save As..." the view "Клин - Клинское"
    When I click on "Enabled Button(View)"
    And I click on "Menu Item(Save As)"
    And I see that "Modal" exists
    And I type "Клин - Клинское" into "Input(New View Name)"
    And I see that "Modal > Radio Button(New)" is checked
    And I see that "Modal > Checkbox(Model Global View)" is checked
    And I click on "Button(Ok)"
    Then I see that "Contents Element(Клин - Клинское)" exists
    And I click on "Tab Header(Клин - Клинское) > Icon(close)"


  Scenario: <3.13> Change view for "Фин. результат"
    When I click on "Contents Element(Фин. результат)"
    And I see that Grid exists and loaded
    And I click on "Enabled Button(Pivot)"

    And I drag "Dnd Element(Versions)" and drop it before "Dnd Element(Cubes)"
    And I see that "Dnd Zone(Rows) > Dnd Element(Versions)" exists

    And I drag "Dnd Element(Бренды)" and drop it before "Dnd Element(Cubes)"
    And I see that "Dnd Zone(Rows) > Dnd Element(Бренды)" exists
    And I click on "Button(Ok)"

    Then I see elements in the grid:
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
    When I click on "Enabled Button(View)"
    And I click on "Menu Item(Save)"
    And I see that "Modal" exists
    And I click on "Modal > Button(Ok)"
    Then I see that "Modal" doesn't exist
    And I click on "Tab Header(Фин. результат) > Icon(close)"
    And I click on "Contents Element(Фин. результат)"
    Then I see elements in the grid:
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
    When I right click on "Col Header(Jun 21)"
    And I click on "Menu Item(Hide)"
    And I see that Grid exists and loaded
    And I see that "Col Header(Jul 21)" exists
    Then I see that "Col Header(Jun 21)" doesn't exist

  Scenario: <3.16> Hide Jul 21 column
    And I right click on "Col Header(Jul 21)"
    And I click on "Menu Item(Hide)"
    And I see that Grid exists and loaded
    And I see that "Col Header(Aug 21)" exists
    Then I see that "Col Header(Jul 21)" doesn't exist

  Scenario: <3.17> Hide Aug 21 column
    And I right click on "Col Header(Aug 21)"
    And I click on "Menu Item(Hide)"
    And I see that Grid exists and loaded
    And I see that "Col Header(Sep 21)" exists
    Then I see that "Col Header(Aug 21)" doesn't exist

  Scenario: <3.18> Hide Sep 21 column
    And I right click on "Col Header(Sep 21)"
    And I click on "Menu Item(Hide)"
    And I see that Grid exists and loaded
    And I see that "Col Header(Oct 21)" exists
    Then I see that "Col Header(Sep 21)" doesn't exist

  Scenario: <3.19> Hide Oct 21 column
    And I right click on "Col Header(Oct 21)"
    And I click on "Menu Item(Hide)"
    And I see that Grid exists and loaded
    And I see that "Col Header(Nov 21)" exists
    Then I see that "Col Header(Oct 21)" doesn't exist

  Scenario: <3.20> Hide Nov 21 column
    And I right click on "Col Header(Nov 21)"
    And I click on "Menu Item(Hide)"
    And I see that Grid exists and loaded
    And I see that "Col Header(Dec 21)" exists
    Then I see that "Col Header(Nov 21)" doesn't exist

  Scenario: <3.21> Hide Dec 21 column
    And I right click on "Col Header(Dec 21)"
    And I click on "Menu Item(Hide)"
    And I see that Grid exists and loaded
    And I see that "Col Header(FY21)" exists
    Then I see that "Col Header(Dec 21)" doesn't exist

  Scenario: <3.22> Unselect details-level "Бренды"
    When I click on "Button(Pivot)"
    And I drag "Dnd Element(Бренды)" and drop it after "Dnd Element(Cubes)"
    And I click on "Button(Ok)"
    Then I see that "Row Header(Клинское)" exists

    When I click on "Row Header(0:-1)"
    And I right click on "Row Header(0:-1)"
    And I click on "Menu Item(Select Level to Show...)"
    And I see that "Modal > Checkbox(details)" is checked
    And I click on "Modal > Checkbox(details)"
    And I click on "Modal > Button(Ok)"
    And I see that Grid exists and loaded
    Then I see that "Row Header(Клинское)" doesn't exist

    When I click on "Row Header(0:-1)"
    And I right click on "Row Header(0:-1)"
    And I click on "Menu Item(Reselect Level)"
    And I wait until modal is opened

    Then I see that "Modal > Checkbox(details)" is not checked
    And I click on "Modal > Button(Cancel)"

  Scenario: <3.23> Create "Data Input Check" view
    When I click on "Button(Pivot)"
    And I wait until modal is opened
    And I drag "Dnd Element(Cubes)" and drop it after "Dnd Element(Бренды)"
    And I click on "Button(Ok)"
    Then I see elements in the grid:
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
    When I click on "Enabled Button(View)"
    And I click on "Menu Item(Save As)"
    And I see that "Modal" exists
    And I type "Data Input Check" into "Input(New View Name)"
    And I see that "Modal > Radio Button(New)" is checked
    And I see that "Modal > Checkbox(Model Global View)" is checked
    And I click on "Button(Ok)"
    Then I see that "Contents Element(Data Input Check)" exists
    And I click on "Tab Header(Data Input Check) > Icon(close)"


  Scenario: <4.1> Open "Доходы" and enter Edit Mode
    When I click on "Contents Element(Доходы)"
    And I see that Grid exists and loaded
    And I click on "Tab Header(Edit Mode)"
    Then I see elements in the grid:
      | 0:-1 | Доходы          |
      | 1:-1 |   Продажи       |
      | 2:-1 |   Upsale        |
      | 3:-1 |   Общие доходы  |

  Scenario: <4.2> Enter formulas for "Доходы"
    When I type "'Продажи' * 0.1" into property "Formula" of element "Upsale"
    And I type "'Продажи' + 'Upsale'" into property "Formula" of element "Общие доходы"
    Then I see elements in the grid:
      | 0:-1 | Доходы          |  |                  |
      | 1:-1 |   Продажи       |  |                  |


  Scenario: <4.3> Check the module structure
    When I click on "Tab Header(Доходы)"
    Then I see elements in the grid:
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
    When I click on "Header Menu Element(Cubes)" in "Header Menu Element(Data)"
    And I see that Grid exists and loaded
    And I type "1000 + 'Затраты на изготовление' * 0.1" into property "Formula" of element "Общезаводские затраты"
    And I type "'Затраты на материалы' + 'Затраты на изготовление' + 'Общезаводские затраты'" into property "Formula" of element "Себестоимость производства"
    And I type "'Доходы'.'Продажи' * 0.05" into property "Formula" of element "Реклама ТВ"
    And I type "600 + 'Производственные затраты'.'Затраты на изготовление' * 0.4" into property "Formula" of element "Затраты на персонал"
    And I type "'Реклама ТВ' + 'Затраты на персонал' + 'Скидки дистрибьюторам'" into property "Formula" of element "Общие накладные затраты"

    When I type "'Доходы'.'Общие доходы'" into property "Formula" of row "15"
    And I type "'Производственные затраты'.'Себестоимость производства' * 1.1" into property "Formula" of element "Заводские расходы"
    And I type "'Накладные расходы'.'Общие накладные затраты'" into property "Formula" of row "17"
    And I type "'Доходы' - 'Заводские расходы' - 'Накладные расходы'" into property "Formula" of element "Чистая прибыль"
    And I type "IF 'Чистая прибыль' > 0 THEN 'Чистая прибыль' * 0.24 ELSE 0" into property "Formula" of element "Налог"
    And I type "('Чистая прибыль' - 'Налог') * 0.3" into property "Formula" of element "Дивиденды"
    Then I see elements in the grid:
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
      | 19:-1 |   Налог                     |  | IF 'Чистая прибыль' > 0 THEN 'Чистая прибыль' * 0.24 ELSE 0                  |
      | 20:-1 |   Дивиденды                 |  | ('Чистая прибыль' - 'Налог') * 0.3                                           |


  Scenario: <4.5> Select style for "Чистая прибыль"
    And I click on "Grid Cell(18:16 )"
    And I click on "Cell Pre Editor > Icon(arrow_drop_down)"
    And I see that "Filter Element(Summary2)" exists
    And I click on "Filter Element(Summary2)"
    Then I see that "Grid Cell(18:16, Summary2)" exists

  Scenario: <4.6> Control Check 0 (checking final results in "Data Input Check")
    When I click on "Contents Element(Data Input Check)"
    And I see that Grid exists and loaded
    Then I see elements in the grid:
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


  Scenario: <4.7> Open and "Доходы - Лента" fill row "Продажи"
    When I click on "Contents Element(Доходы - Лента)"
    And I change filter "Total Company" to "Лента"
    And I click on "Enabled Button(View)"
    And I click on "Menu Item(Save)"
    And I see that "Modal" exists
    And I click on "Modal > Button(Ok)"
    And I see that "Modal" doesn't exist
    And I see that Grid exists and loaded
    And I type "100" into property "Jan 21" of row "1"
    And I see that "Grid Cell(1:0, 100)" exists
    And I click on "Grid Cell (1:0)"
    And I click on "Enabled Button(Copy Right)"
    And I see that "Grid Cell(1:1, 100)" exists
    Then I see elements in the grid:
      | 0:-1  | Total Brands | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
      | 1:-1  | Клинское     | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
      | 2:-1  | Толстяк      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 3:-1  | Балтика      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 4:-1  | Total Brands | 10  | 10  | 10  | 10  | 10  | 10  | 10  | 10  |
      | 5:-1  | Клинское     | 10  | 10  | 10  | 10  | 10  | 10  | 10  | 10  |
      | 6:-1  | Толстяк      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 7:-1  | Балтика      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 8:-1  | Total Brands | 110 | 110 | 110 | 110 | 110 | 110 | 110 | 110 |
      | 9:-1  | Клинское     | 110 | 110 | 110 | 110 | 110 | 110 | 110 | 110 |
      | 10:-1 | Толстяк      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 11:-1 | Балтика      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |


  Scenario: <4.8> Change the pivot
    When I click on "Button(Pivot)"
    And I drag "Dnd Element(Бренды)" and drop it into "Dnd Zone(Pages)"
    And I see that "Dnd Zone(Pages) > Dnd Element(Бренды)" exists
    And I click on "Button(Ok)"
    And I change filter "Total Brands" to "Клинское"
    And I change filter "Total Company" to "Лента"
    Then I see elements in the grid:
      | 0:-1 | Продажи      | 100 | 100 | 100 | 100 | 100 | 100 | 100 | 100 |
      | 1:-1 | Upsale       | 10  | 10  | 10  | 10  | 10  | 10  | 10  | 10  |
      | 2:-1 | Общие доходы | 110 | 110 | 110 | 110 | 110 | 110 | 110 | 110 |
      | 3:-1 | Продажи      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 4:-1 | Upsale       | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 5:-1 | Общие доходы | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 6:-1 | Продажи      | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 7:-1 | Upsale       | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
      | 8:-1 | Общие доходы | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |


  Scenario: <4.9> Fill in more cells for Current Plan and Previous Plan
    When I type "0" into property "May 21" of row "0"
    And I see that "Grid Cell(0:4, 0)" exists
    And I click on "Grid Cell (0:4)"
    And I click on "Enabled Button(Copy Right)"
    Then I see that "Grid Cell(0:5, 0)" exists

    When I type "150" into property "May 21" of row "3"
    And I see that "Grid Cell(3:4, 150)" exists
    And I click on "Grid Cell (3:4)"
    And I click on "Enabled Button(Copy Right)"
    And I see that "Grid Cell(3:5, 150)" exists
    Then I see elements in the grid:
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
    When I click on "Contents Element(Data Input Check)"
    And I see that Grid exists and loaded
    Then I see elements in the grid:
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
    When I click on "Contents Element(Доходы)"
    And I see that Grid exists and loaded
    And I change filter "Total Company" to "Лента"
    And I change filter "Total Brands" to "Клинское"
    And I see that Grid exists and loaded
    And I click on "Grid Cell(0:0)"
    And I type "15000" into property "Jan 21" of row "0"
    Then I see elements in the grid:
      | 0:-1 | Продажи      | 15 000 |

    When I type "16000" into property "Feb 21" of row "0"
    Then I see elements in the grid:
      | 0:-1 | Продажи      | 15 000 | 16 000 |

    When I type "15000" into property "Mar 21" of row "0"
    Then I see elements in the grid:
      | 0:-1 | Продажи      | 15 000 | 16 000 | 15 000 |

    When I type "18500" into property "Apr 21" of row "0"
    Then I see elements in the grid:
      | 0:-1 | Продажи      | 15 000 | 16 000 | 15 000 | 18 500 |

    When I type "18000" into property "May 21" of row "3"
    Then I see elements in the grid:
      | 3:-1 | Продажи      |  |  |  |  | 18 000 |

    When I click on "Grid Cell(3:4)"
    And I click on "Button(Copy Right)"
    Then I see elements in the grid:
      | 3:-1 | Продажи      |  |  |  |  | 18 000 | 18 000 |

  Scenario: <4.12> Control Check 2 (checking final results in "Data Input Check")
    When I click on "Contents Element(Data Input Check)"
    And I see that Grid exists and loaded
    Then I see elements in the grid:
      | 0:-1  | Доходы            | 16 500  | 17 600  | 16 500  | 20 350  | 0         | 70 950    | 70 950   | 0         |
      | 1:-1  | Заводские расходы | 9 900   | 9 900   | 9 900   | 9 900   | 9 900     | 118 800   | 39 600   | 79 200    |
      | 2:-1  | Накладные расходы | 2 550   | 2 600   | 2 550   | 2 725   | 1 800     | 24 825    | 10 425   | 14 400    |
      | 3:-1  | Чистая прибыль    | 4 050   | 5 100   | 4 050   | 7 725   | -11 700   | -72 675   | 20 925   | -93 600   |
      | 4:-1  | Налог             | 2 844   | 3 096   | 2 844   | 3 726   | 0         | 12 510    | 12 510   | 0         |
      | 5:-1  | Дивиденды         | 362     | 601     | 362     | 1 200   | -3 510    | -25 555   | 2 524    | -28 080   |

  Scenario: <4.13> Fill the module "Накладные расходы - Клинское"
    When I click on "Contents Element(Накладные расходы - Клинское)"
    And I see that Grid exists and loaded
    Then I see elements in the grid:
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

    When I click on "Grid Cell(2:0)"
    And I type "300" into property "Jan 21" of row "2"
    And I see that Grid exists and loaded
    And I type "300" into property "Feb 21" of row "2"
    And I see that Grid exists and loaded
    And I type "300" into property "Mar 21" of row "2"
    And I see that Grid exists and loaded
    And I type "300" into property "Apr 21" of row "2"
    And I see that Grid exists and loaded
    And I type "500" into property "May 21" of row "6"
    Then I see elements in the grid:
      | 6:-1  | Скидки дистрибьюторам   |  |  |  |  | 500 |

    When I click on "Grid Cell(6:4)"
    And I click on "Button(Copy Right)"
    Then I see elements in the grid:
      | 6:-1  | Скидки дистрибьюторам   |  |  |  |  | 500 | 500 |

    Then I see elements in the grid:
      | 0:-1  | Реклама ТВ              | 750   | 800   | 750   | 925   | 0     | 0     | 0     | 0     |
      | 1:-1  | Затраты на персонал     | 600   | 600   | 600   | 600   | 600   | 600   | 600   | 600   |
      | 2:-1  | Скидки дистрибьюторам   | 300   | 300   | 300   | 300   | 0     | 0     | 0     | 0     |
      | 3:-1  | Общие накладные затраты | 1 650 | 1 700 | 1 650 | 1 825 | 600   | 600   | 600   | 600   |
      | 4:-1  | Реклама ТВ              | 0     | 0     | 0     | 0     | 900   | 900   | 900   | 900   |
      | 5:-1  | Затраты на персонал     | 600   | 600   | 600   | 600   | 600   | 600   | 600   | 600   |
      | 6:-1  | Скидки дистрибьюторам   | 0     | 0     | 0     | 0     | 500   | 500   | 500   | 500   |
      | 7:-1  | Общие накладные затраты | 600   | 600   | 600   | 600   | 2 000 | 2 000 | 2 000 | 2 000 |

  Scenario: <4.14> Control Check 3 (checking final results in "Data Input Check")
    When I click on "Contents Element(Data Input Check)"
    Then I see elements in the grid:
      | 0:-1  | Доходы            | 16 500  | 17 600  | 16 500  | 20 350  | 0         | 70 950    |
      | 1:-1  | Заводские расходы | 9 900   | 9 900   | 9 900   | 9 900   | 9 900     | 118 800   |
      | 2:-1  | Накладные расходы | 2 850   | 2 900   | 2 850   | 3 025   | 1 800     | 26 025    |
      | 3:-1  | Чистая прибыль    | 3 750   | 4 800   | 3 750   | 7 425   | -11 700   | -73 875   |
      | 4:-1  | Налог             | 2 772   | 3 024   | 2 772   | 3 654   | 0         | 12 222    |
      | 5:-1  | Дивиденды         | 293     | 533     | 293     | 1 131   | -3 510    | -25 829   |


  Scenario: <4.15> Fill the module "Производственные затраты"
    When I click on "Contents Element(Клин - Клинское)"
    Then I see elements in the grid:
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


    When I click on "Grid Cell(0:0)"
    And I type "400" into property "Jan 21" of row "0"
    And I see that Grid exists and loaded
    And I type "300" into property "Feb 21" of row "0"
    And I see that Grid exists and loaded
    And I type "400" into property "Mar 21" of row "0"
    And I see that Grid exists and loaded
    And I type "500" into property "Apr 21" of row "0"
    And I see that Grid exists and loaded
    And I type "150" into property "Jan 21" of row "1"
    And I see that Grid exists and loaded
    And I type "250" into property "Feb 21" of row "1"
    And I see that Grid exists and loaded
    And I type "800" into property "Mar 21" of row "1"
    And I see that Grid exists and loaded
    And I type "100" into property "Apr 21" of row "1"
    And I see that Grid exists and loaded
    And I type "450" into property "May 21" of row "4"
    Then I see elements in the grid:
      | 4:-1  |  |  |  |  |  | 450 |

    When I click on "Grid Cell(4:4)"
    And I click on "Button(Copy Right)"
    Then I see elements in the grid:
      | 4:-1  |  |  |  |  |  | 450 | 450 |

    When I type "225" into property "May 21" of row "5"
    Then I see elements in the grid:
      | 5:-1  |  |  |  |  |  | 225 |

    When I click on "Grid Cell(5:4)"
    And I click on "Button(Copy Right)"
    Then I see elements in the grid:
      | 5:-1  |  |  |  |  |  | 225 | 225 |

    Then I see elements in the grid:
      | 0:-1  | Затраты на материалы       | 400   | 300   | 400   | 500   | 0       | 0       | 0       | 0       | 0       | 0       | 0       |
      | 1:-1  | Затраты на изготовление    | 150   | 250   | 800   | 100   | 0       | 0       | 0       | 0       | 0       | 0       | 0       |
      | 2:-1  | Общезаводские затраты      | 1 015 | 1 025 | 1 080 | 1 010 | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   |
      | 3:-1  | Себестоимость производства | 1 565 | 1 575 | 2 280 | 1 610 | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   | 1 000   |
      | 4:-1  | Затраты на материалы       |  0    | 0     | 0     | 0     | 450     | 450     | 450     | 450     | 450     | 450     | 450     |
      | 5:-1  | Затраты на изготовление    |  0    | 0     | 0     | 0     | 225     | 225     | 225     | 225     | 225     | 225     | 225     |
      | 6:-1  | Общезаводские затраты      | 1 000 | 1 000 | 1 000 | 1 000 | 1 023   | 1 023   | 1 023   | 1 023   | 1 023   | 1 023   | 1 023   |
      | 7:-1  | Себестоимость производства | 1 000 | 1 000 | 1 000 | 1 000 | 1 698   | 1 698   | 1 698   | 1 698   | 1 698   | 1 698   | 1 698   |


  Scenario: <4.16> Control Check 4 (checking final results in "Data Input Check")
    When I click on "Contents Element(Data Input Check)"
    Then I see elements in the grid:
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

  Scenario: <5.1> Revert model
    When I click on "Header Menu Element(Logs)" in "Header Menu Element(Security Center)"
    And I see that Grid exists and loaded
    Then I see that "Row Header(2, 0:-1)" exists
    Then I see that "Row Header(1, 1:-1)" exists

    When I click on "Row Header(1:-1)"
    And I click on "Button(Restore)"
    And I click on "Modal > Input"
    And I type "1"
    And I click on "Modal > Button(Restore)"
    And I see that "Global Loader" exists
    And I see that "Global Loader" doesn't exist
    And I see that Grid exists and loaded
    Then I see that "Row Header(1, 0:-1)" exists
    Then I see that "Row Header(2)" doesn't exist

#  Scenario: <Service>  I destroy environment
#    Then Destroy feature model
```


[Оглавление](../README.md)