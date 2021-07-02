# Специфические шаги

## 1)    And I don't see element "Card of Dashboards(1.1 Страны) > Loader" now
## 2)    And I see that "Global Loader" doesn't exist for a long time
## 3)    And I reload app
## 4)    When I refresh page
## 5)    Given I am on the "Drive Landing" page
## 6)    Given I am on the "Basic Module" module
## 7)    Given I am on the "Dashboard with Data" dashboard
## 8)    And I clear temp model at current workspace
## 9)    And I wait until modal is opened
## 10)    And I clear "([^"]*)" input
## 11)    And I see that "Tab Header" with text "Half Years" is active
## 12)    And I see that "Tab Header" with text "Half Years" is not active
## 13)    And I scroll vertical scroller to element ""
## 14)    When I scroll kanban vertical scroller to down
## 15)    When I scroll kanban horizontal scroller to end
## 16)    And I call the context menu with hot keys - Вызов диалогового окна по CTRL + Q
## 17)    And I run action "Default Action" - Запуск акшена по кнопке Run в Toolbar
## 18)    And I submit the form - Шаг кликает по кнопке Sabmit
## 19)    When I set "Time Period coll empty" to "Feb 19" for element "В2" without update cell
## 20)    When I type "66000000" into property "Стоимость производства" of element "Jan 17" without update checking
## 21)    And I see that size prop "width" of element "Col Header(Line Item Text)" is [81] Ширина колонки
## 22)    Then I see that css prop "left" of element "Selection Body Layout" is [243px] - Проверка пропертри у css свойства элемента
## 23)    And I see that grid has right spaces - Проверка того что в конце грида снизу или справа есть отступ
## 24)    Then I see that grid has down spaces - Проверка того что в конце грида снизу или справа есть отступ
## 25)    And I drag "Zoom Slider" and see value [1] - Шаг для увеличения или уменьшения размера приложения в настройках
## 26)    And I set viewport width [1366] and height [620] - Если понадобилось запустить тест с другим размером браузера. Дефолтно запускается с 1920x1080
## 27)    When I stretch element "Col Header(-2:4|Line Item 3)" to the "right" by [48] - Шаг для растягивания элементов в нужном направлении на нужное колличество px
## 28)    Then I see that height of element "Constraints Formula Line" is equal to [213] - Проверка высоты поля ввода в гриде Optimizer
## 29)    And I see that Grid exists and loaded in [15] seconds

    Шаг выполняет провергу загрузки грида в течении 15 секунд. Если за 15 секунд грид не загрузился, то шаг упадет. Выставить мы можем время в пределах 60 секунд



## 30) And I paste after hash in url "eyJ0eXBlIjoiTXVsdGljdWJlc0RhdGFCdWlsZGVyVGFiIiwicGFyYW1zIjp7InRpdGxlIjoiTXVsdGljdWJlcyIsImFjdGl2ZVRhYiI6MH19"

Шаг вставляет дополнительный хеш в адресную строку браузера после ID модели и символа # - Этот шаг нужен для тестирования роутинга
    
## 31) When I remove hash from url - Шаг удалит хэш

    
## 32) And I set to input "Grid Settings Input" value:
```JavaScript 
And I set to input "Grid Settings Input" value:
      """
      { "defaultCellWidth": 90, "defaultCellHeight": 30 }
      """
```


## 33) Then I see in input "Formula Input" value:
```JavaScript 
Then I see in input "Formula Input" value:
"""
    =	 100+
100+
100
"""
```


## 34) Then I see in element "Grid Cell(2:1)" title:
```JavaScript 
Then I see in element "Grid Cell(2:1)" title:
"""
sdfsdfjsd;lkfjsdlkfjsdlkfj sdfsdfsdfaaaaajkhkjhsdfkljsdhflksdjhfksdljfhksdjfh

sdfsdlkfjsdlkfj lksdjf;sdlkjflkjlksdjf skdfjlsdkfjsd;lfjksdlfj dsfjsdlfkjsdf
"""
```


## 35) When I insert elements after "Улицы":
```JavaScript 
When I insert elements after "Улицы":
      """
      Материалы
      2.1 Регионы
      """
```


## 36) > When I drop file "E2E Test Model.zip" to the "Drive Landing"
> When I drop file "Nomenklatura.xlsx" to the "Grid"

Шаги для переноса файлов из папки Fixtures в наш грид или еще какую-то область. Это позволяет сделать импорт подготовленного файла

## 37) > Then I compare "Grid Container" with "conditional-formatting-for-row-where-exist-cell-with-preset.png"

Шаг для сравнения эталонного скриншота с тем скриншотом который будет делаться при прогоне теста.
Сам шаг довольно специфический. Есть много нюансов, раскажу несколько из них!
Чтобы сделать скриншот эталонный, нужно прогнать сам тест, забрать сделанный скриншот из репорта, положить его в проект в папку screanshots и в следующих запусках теста, шаг уже будет сравнивать один скриншот со вторым.


# Сервисные шаги
## 1)    Given Isolated "E2E Test Model" model
## 2)    Given Not isolated "E2E Context Hard Test" model
## 3)    Given App as "modeller"
## 4)    Then Destroy feature model


[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)