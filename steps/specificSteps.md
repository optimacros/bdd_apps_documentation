# Специфические шаги

## 1)    And I don't see element "Card of Dashboards(1.1 Страны) > Loader" now

Отстуствие элемента на странице в данный момент вермени!

## 2)    And I see that "Global Loader" doesn't exist for a long time

Проверка на то что элемент отсуствует с задежкой по таймауту, т.е. вместо обычных 60 секунд, шаг будет ждать 3 минуты

## 3)    And I reload app

Перезагрузка приложения
## 4)    When I refresh page

Перезагрузка приложения

## 5)    Given I am on the "Drive Landing" page

Открыть страницу Drive Landing или Main

## 6)    Given I am on the "Basic Module" module

Открое какой-либо элемент с указанным именем. Шаг выберет элемент из списка в поле Contents, перед этим произойдет перезагрузка страницы, вызывет страницу Main

## 7)    Given I am on the "Dashboard with Data" dashboard

Открое какой-либо элемент с указанным именем. Шаг выберет элемент из списка в поле Contents, перед этим произойдет перезагрузка страницы, вызывет страницу Main

## 8)    And I clear temp model at current workspace

Очистка временных моделей (копии моделей с хешом и другие модели с хешом)

## 9)    And I wait until modal is opened

Ожидание открытия модального окна

## 10)    And I clear "([^"]*)" input

Очистка значения в поле input. В качестве аргумента указывается атрибут Name нужного input

## 11)    And I see that "Tab Header" with text "Half Years" is active

Проверка на то, активен ли таб

## 12)    And I see that "Tab Header" with text "Half Years" is not active

Проверка на то, не активен ли таб

## 13)    And I scroll vertical scroller to element ""

Проскролить до нужной строки с названием

## 14)    When I scroll kanban vertical scroller to down

Вертикальный скролл в Kanban

## 15)    When I scroll kanban horizontal scroller to end

Горизонтальный скролл в Kanban

## 16)    And I call the context menu with hot keys

Вызов диалогового окна по CTRL + Q

## 17)    And I run action "Default Action"

Запуск акшена по кнопке Run в Toolbar

## 18)    And I submit the form

Шаг кликает по кнопке Sabmit

## 19)    When I set "Time Period coll empty" to "Feb 19" for element "В2" without update cell

Выбор из выпадающего списка открывающегося на пересечении колонки и строки без ожидания лоадера и пауз в конце шага.
- Первый аргумент название колонки
- Далее элемент из выпадающего списка
- Далее указываем название строки

## 20)    When I type "66000000" into property "Стоимость производства" of element "Jan 17" without update checking

Ввод в клетку текста на пересечении колонки и строки без ожидания лоадера и пауз в конце шага.
- Первый аргумент это текст который хотим ввести в клетку
- Далее название колонки
- И указываем название строки

## 21)    And I see that size prop "width" of element "Col Header(Line Item Text)" is [81]

Ширина в px у опредленной колонки. Можно в качестве агрумента передать и другое свойство



## 22)    Then I see that css prop "left" of element "Selection Body Layout" is [243px]

Проверка пропертри у css свойства элемента

## 23)    And I see that grid has right spaces 

Проверка того что в конце грида снизу или справа есть отступ

## 24)    Then I see that grid has down spaces

Проверка того что в конце грида снизу или справа есть отступ

## 25)    And I drag "Zoom Slider" and see value [1]

Шаг для увеличения или уменьшения размера приложения в настройках

## 26)    And I set viewport width [1366] and height [620]

Если понадобилось запустить тест с другим размером браузера. Дефолтно запускается с 1920x1080

## 27)    When I stretch element "Col Header(-2:4|Line Item 3)" to the "right" by [48]

Шаг для растягивания элементов в нужном направлении на нужное колличество px

## 28)    Then I see that height of element "Constraints Formula Line" is equal to [213]

Проверка высоты поля ввода в гриде Optimizer

## 29)    And I see that Grid exists and loaded in [15] seconds

    Шаг выполняет провергу загрузки грида в течении 15 секунд. Если за 15 секунд грид не загрузился, то шаг упадет. Выставить мы можем время в пределах 60 секунд

## 30) And I paste after hash in url "eyJ0eXBlIjoiTXVsdGljdWJlc0RhdGFCdWlsZGVyVGFiIiwicGFyYW1zIjp7InRpdGxlIjoiTXVsdGljdWJlcyIsImFjdGl2ZVRhYiI6MH19"

Шаг вставляет дополнительный хеш в адресную строку браузера после ID модели и символа # - Этот шаг нужен для тестирования роутинга
    
## 31) When I remove hash from url

Шаг удалит хэш после id модели

## 32) And I set to input "Grid Settings Input" value:
```JavaScript 
And I set to input "Grid Settings Input" value:
      """
      { "defaultCellWidth": 90, "defaultCellHeight": 30 }
      """
```
Шаг возможно не работает.. Вводил текст в инпут

## 33) Then I see in input "Formula Input" value:
```JavaScript 
Then I see in input "Formula Input" value:
"""
    =	 100+
100+
100
"""
```

Шаг проверяет отступы и текст в инпуте


## 34) Then I see in element "Grid Cell(2:1)" title:
```JavaScript 
Then I see in element "Grid Cell(2:1)" title:
"""
sdfsdfjsd;lkfjsdlkfjsdlkfj sdfsdfsdfaaaaajkhkjhsdfkljsdhflksdjhfksdljfhksdjfh

sdfsdlkfjsdlkfj lksdjf;sdlkjflkjlksdjf skdfjlsdkfjsd;lfjksdlfj dsfjsdlfkjsdf
"""
```

Шаг проверяет value элементов с отсутпами и всем текстом


## 35) When I insert elements after "Улицы":
```JavaScript 
When I insert elements after "Улицы":
      """
      Материалы
      2.1 Регионы
      """
```
Шаг по инсерту элементов после строки с названием Улицы

## 36) > When I drop file "E2E Test Model.zip" to the "Drive Landing"
When I drop file "Nomenklatura.xlsx" to the "Grid"

Шаги для переноса файлов из папки Fixtures в наш грид или еще какую-то область. Это позволяет сделать импорт подготовленного файла

## 37) > Then I compare "Grid Container" with "conditional-formatting-for-row-where-exist-cell-with-preset.png"

Шаг для сравнения эталонного скриншота с тем скриншотом который будет делаться при прогоне теста.
Сам шаг довольно специфический. Есть много нюансов, раскажу несколько из них!
Чтобы сделать скриншот эталонный, нужно прогнать сам тест, забрать сделанный скриншот из репорта, положить его в проект в папку screanshots и в следующих запусках теста, шаг уже будет сравнивать один скриншот со вторым.


# Сервисные шаги

## 1)    Given Isolated "E2E Test Model" model

Создание изолированной модели

## 2)    Given Not isolated "E2E Context Hard Test" model

Создание не изолированной модели

## 3)    Given App as "modeller"

Открытие приложения из под определенного пользоваля. Используем для проверки функционала из под пользователей с разными правами - моделлеры, не моделлеры, лимитированные пользователе

## 4)    Then Destroy feature model

Удаление ранее созданной изолированной копии модели. Нужно быть осторожным, если вы запустите тест в оригинальной модели, то шаг удалит вашу модель!

[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)