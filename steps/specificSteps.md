# Специфические шаги

## 1)    * Check if element "Selector" is visible now
* Check if element "Card of Dashboards(1.1 Страны) > Loader" is visible now
Отстуствие элемента на странице в данный момент вермени!

## 2)    * Check if "Selector" does not exist for a long time
Проверка на то что элемент отсуствует с задежкой по таймауту, т.е. вместо обычных 60 секунд, шаг будет ждать 3 минуты

## 3)    * Reload Page
Перезагрузка приложения

## 5)    * Go to page "PageName"
Открыть страницу Drive Landing или Main

## 6)    * Open tab "ModuleName"
Откроет какой-либо элемент с указанным именем. Шаг выберет элемент из списка в поле Contents, перед этим произойдет перезагрузка страницы

## 7) * Close tab "ModuleName"
Зкарывает указанный таб

## 8) * Wait [Number] seconds
Ожидание в секундах

## 8)    * Clean temp models in current workspace
Очистка временных моделей (копии моделей с хешом и другие модели с хешом)

## 9)    * Wait until the modal form is open
Ожидание открытия модального окна

## 10)   * Clear "Selector"
* Clear "Conditional Formatting(Maximum) > Input"
Очистка значения в поле input. В качестве аргумента указывается атрибут Name нужного input

## 11)    * Check if "Selector" with text "Text" is active
Используется для роверки на то, активен ли таб

## 12)    * Check if "Selector" with text "Text" is not active
* Check if "Tab Header" with text "Half Years" is not active
Проверка на то, не активен ли таб

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

## 16)    * Open the context menu with a hotkey
Вызов диалогового окна по CTRL + Q со списком измерений

## 17)    And I run action "Default Action"
Запуск акшена по кнопке Run в Toolbar грида Actions

## 18)   * Submit the form
Шаг кликает по кнопке Sabmit

## 19)   * Set "Value" of the cell at the intersection of "CollName" and "RowName" without updating the cell
Выбор из выпадающего списка открывающегося на пересечении колонки и строки без ожидания лоадера и пауз в конце шага.


## 20) * Set "Value" of the cell at the intersection of "CollName" and "RowName"
Выбрать опцию в выпадающем списке на пересечении Колонки и Строки

## 20) * Set "Value" of the cell at the intersection of "CollName" and "RowName" without updating the cell
Выбрать опцию в выпадающем списке на пересечении Колонки и Строки без ожидания обновления грида

## 20) * Insert "Text" into the cell at the intersection of "CollName" and "RowName"
Ввод в клетку текста на пересечении колонки и строки без ожидания лоадера и пауз в конце шага.


## 20) * Insert "Text" into the cell at the intersection of "CollName" and "RowName" without updating the cell
Ввод в клетку текста на пересечении колонки и строки без ожидания лоадера и пауз в конце шага.

## 21)    * Check if "width" of "Selector" equals to [Number]
* Check if "width" of "Col Header(Line Item Text)" to [81]
Ширина в px у опредленной колонки. Можно в качестве агрумента передать и другое свойство


## 22)    * Check if CSS style "top" of "Selector" equals to [Number] exists
Then I see that css prop "left" of element "Selection Body Layout" is [243px]
Проверка пропертри у css свойства элемента

## 23)    * Check that grid has right spaces
Проверка того что в конце грида справа есть отступ

## 24)    * Check that grid has down spaces
Проверка того что в конце грида снизу есть отступ

## 25)    * Drag "Selector" and set the value equal to [Number]
* Drag "Zoom Slider" and set the value equal to [1]
Шаг для увеличения или уменьшения размера приложения в настройках пользователя.

## 26)   * Set viewport width [Pixels] and height [Pixels] pixels
Если понадобилось запустить тест с другим размером браузера. Дефолтно запускается с 1920x1080

## 27)   * Stretch element "Selector" [Pixels] pixels to the "left"
Шаг для растягивания элементов в нужном направлении на нужное колличество px
* Stretch element "Selector" [Pixels] pixels to the "right"
* Stretch element "Selector" [Pixels] pixels to the "top"
* Stretch element "Selector" [Pixels] pixels to the "bottom"

## 28)    * Check that height of the "Selector" is equal to [Number]
* Check that height of the "Constraints Formula Line" is equal to [213]
Проверка высоты поля ввода в гриде Optimizer

## 29)    * Check if the Grid exists and loaded after [Number] second (s)
Шаг выполняет провергу загрузки грида в течении *** секунд. Если за *** секунд грид не загрузился, то шаг упадет. Выставить мы можем время в пределах 60 секунд

## 30)  * Paste "Text" after hash in the url
 * Paste "eyJ0eXBlIjoiTXVsdGljdWJlc0RhdGFCdWlsZGVyVGFiIiwicGFyYW1zIjp7InRpdGxlIjoiTXVsdGljdWJlcyIsImFjdGl2ZVRhYiI6MH19" after hash in the url
Шаг вставляет дополнительный хеш в адресную строку браузера после ID модели и символа # - Этот шаг нужен для тестирования роутинга
    
## 31) * Remove hash from the url
Шаг удалит хэш после id модели

## 32) * Set the value to "Selector":
```JavaScript 
* Set the value to "Grid Settings Input":
      """
      { "defaultCellWidth": 90, "defaultCellHeight": 30 }
      """
```
Шаг возможно не работает.. Он вводил текст в инпут

## 33) * Check if "Selector" contains value:
```JavaScript 
* Check if "Formula Input" contains value:
"""
    =	 100+
100+
100
"""
```
Шаг проверяет отступы и текст в инпуте


## 34) * Check if "Selector" title matches:

```JavaScript 
* Check if "Grid Cell(2:1)" title matches:
"""
sdfsdfjsd;lkfjsdlkfjsdlkfj sdfsdfsdfaaaaajkhkjhsdfkljsdhflksdjhfksdljfhksdjfh

sdfsdlkfjsdlkfj lksdjf;sdlkjflkjlksdjf skdfjlsdkfjsd;lfjksdlfj dsfjsdlfkjsdf
"""
```
Шаг проверяет value элементов с отсутпами и всем текстом


## 35) * Drop file "File" to "Selector"
When I drop file "Nomenklatura.xlsx" to the "Grid"

Шаги для переноса файлов из папки Fixtures в наш грид или еще какую-то область. Это позволяет сделать импорт подготовленного файла

## 36) * Compare "Selector" with "File.png"
Шаг для сравнения эталонного скриншота с тем скриншотом который будет делаться при прогоне теста.
Сам шаг довольно специфический. Есть много нюансов, раскажу несколько из них!
Чтобы сделать скриншот эталонный, нужно прогнать сам тест, забрать сделанный скриншот из репорта, положить его в проект в папку screanshots и в следующих запусках теста, шаг уже будет сравнивать один скриншот со вторым.

## 37) * Screenshot page "File.png"

## 38) * Check if the style in "Selector" matches "Style"
* Check style "heading1" in "Grid Cell(0:13)"
Проверка стиля в ячейке по координатам

## 39) * Check if the style in "Selector" does not match "Style"
Проверка отсуствия стиля в ячейке по координатам

## 39) * Scroll the vertical scroller to the element "Selector"
Проскролить грид по вертикали к указанному элементу. Грид должен быть прогружен если элемент ниже видимой области..


# Сервисные шаги

## 1)    * Start with an isolated model "ModelName"
Создание изолированной модели

## 2)    * Start with a not isolated model "ModelName"
Создание не изолированной модели

## 3)    * Start as a "User"
Открытие приложения из под определенного пользоваля. Используем для проверки функционала из под пользователей с разными правами - моделлеры, не моделлеры, лимитированные пользователи

## 4)    * Delete the current model
Удаление ранее созданной изолированной копии модели самим тестом. ***Нужно быть осторожным, если вы запустите тест в оригинальной модели, то шаг удалит вашу модель!***

[Список всех шагов](../steps/allSteps.md)

[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)