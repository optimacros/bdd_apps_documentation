# Advanced-шаги (иногда могут понадобиться)
[1. Сервисные шаги]
[2. Действия с элементами]
[3. Работа с буфером обмена]
[4. Проверка существования элементов]
[5. Шаги связанные с публикацией]
[6. Прочие шаги]


## 1. Сервисные шаги

### 1.1. * Close tab "ModuleName"
Закрывает вкладку с именем
```
* Close tab "Заявки"
* Close tab "Main Dashboard"
```

### 1.2. * Wait [Number] second(s)
Делает паузу в сценарии
```
* Wait [2] seconds
* Wait [1] second
```

## 2. Действия с элементами

### 2.1. * Click using coordinates "X:Y"
Делает клик левой кнопкой мыши, используя координаты. Чаще применяется для графиков
```
* Click using coordinates "445:408"
```

### 2.2. * Right click using coordinates "X:Y"
Делает клик правой кнопкой мыши, используя координаты. Чаще применяется для графиков
```
* Right click using coordinates "696:490"
```

### 2.3. * Hover over coordinates "X:Y"
Наводит курсор мыши на координаты. Обычно применяется в графиках
```
* Hover over coordinates "150:333"
```

### 2.4. * Stretch element "Selector" [Pixels] pixels to the "left/right/top/bottom"
Растягивает выбранный элемент влево, вправо, вверх или вниз на определенное количество пикселей
```
* Stretch element "Dashboard Card With Id Name(textarea4)" [300] pixels to the "left"
* Stretch element "Col Header(-1:4|May 16)" [30] pixels to the "right"
* Stretch element "Variables Formula Line Resizier" [50] pixels to the "top"
* Stretch element "Row Header(2:-1)" [39] pixels to the "bottom"
```

### 2.5. * Open cells settings at position “X:Y”
Открывает cells settings в ячейке с позицией X Y
```
* Open cells settings at position “3:1”
```

## 3. Работа с Буфером Обмена

### 3.1. * Clear Clipboard
Очищает буфер обмена.

### 3.2. * Check if the clipboard contains "Text"
Проверяет что буфер обмена содержит текст
```
* Check if the clipboard contains "13.12.2019"
```

### 3.3. * Check if the clipboard does not contain "Text"
Проверяет что буфер обмена не содержит текст
```
* Check if the clipboard does not contain "Forecast"
```

### 3.4. * Check if the clipboard is empty
Проверяет что буфер обмена пустой

### 3.5. * Paste from clipboard
Вставляет данные из буфера обмена

### 3.6. * Copy data from "f:File.csv" to clipboard
Копирует в буфер обмена данные из файла csv
```
* Copy data from "f:TestEditableModuleData.csv" to clipboard
```

### 3.7. * Copy to clipboard:
Копирует в буфер обмена значения таблицы
```
* Copy to clipboard:
| 100    | 200     | 300     |
| Text 1 | Text 2  | Text 3  |
```

### 3.8. * Copy selection to the clipboard
Копирует выделенное в буфер обмена

### 3.9. * Fill the cells with data from the clipboard
Вставляет в ячейки данные из буфера обмена и ожидает появление данных в ячейках

### 3.10. * Fill the cells with data from the clipboard without waiting
Вставляет в ячейки данные из буфера обмена без ожидания появления данных в ячейках

### 3.11. * Fill the grid with data from "f:File.csv"
Вставка в грид данных из файла csv

## 4. Проверка существования элементов

### 4.1. * Check if "Selector" exists for a long time
Проверяет существование элемента на странице. В этом шаге увеличен таймаут до 180 секунд, для проверки элементов с долгим отображением
```
* Check if "Filter(Total Company)" exists for a long time
```

### 4.2. * Check if "Selector" does not exist for a long time
Проверяет отсутствие элемента на странице. В этом шаге увеличен таймаут до 180 секунд, для проверки отсутствия элемента длительное время
```
* Check if "Global Loader" doesn't exist for a long time
```

### 4.3. * Check if "Selector" exists now
Утверждает присутствие элемента сейчас
```
* Check if "Card Of Dashboards(Chart m3 filter List) > Loader" exists now
```

### 4.4. * Check if "Selector" does not exist now
Проверяет, что элемент отсутствует сейчас
```
* Check if "Grid > Loader" does not exist now
```

### 4.5. *Check if "Selector" does not exist for [Number] seconds
Проверяет, что элемент отсутствует определенное время
```
* Check if "Any Loader" does not exist for [1] second
```

### 4.6. * Check if the value is empty in "Selector"
Проверяет что в инпут не введено никаких значений
```
* Check if the value is empty in "Formula Input"
```

### 4.5. * Сheck if "Selector" is checked
### * Сheck if "Selector" is not checked
### * Сheck if "Selector" is disabled
### * Сheck if "Selector" is not disabled
### * Сheck if "Selector" is active
### * Сheck if "Selector" is selected
Шаги проверяют свойства элементов
```
* Сheck if "GridCell(4:2) > Checkbox" is checked
* Сheck if "Modal > Checkbox(summaries)" is not checked
* Сheck if "Toolbar > Button(Open)" is disabled
* Сheck if "Modal > Input(password)" is not disabled
* Сheck if "Modal > Tab Header(Advanced)" is active
* Сheck if "Modal > Tree Menu Element(test property for update)" is selected
```

## 5. Шаги связанные с публикацией

### 5.1 * Publish the current chart to dashboard "dashboardName"
Публикует график на указанный Дашборд
Шаг включает в себя нажатие на кнопку View в модальном окне с графиком > в дропдауне Publish to Dashboard выбирает указанный Дашборд.
Проверяет глобальный лоадер
```
* Publish the current chart to dashboard "Chart Dashboard"
```
Когда лоадер не появляется при публикации используем шаг:
```
* Publish the current chart to dashboard "Chart Dashboard" without loader
```

### 5.3 * Publish the current chart to context table "contextTableName"
Публикует график на указанную контекстную таблицу
Шаг включает в себя нажатие на кнопку View в модальном окне с графиком > в дропдауне Publish to Context Table выбирает указанную контекстную таблицу
Проверяет глобальный лоадер
```
* Publish the current chart to context table "CT for test"
```
Когда лоадер не появляется при публикации используем шаг:
```
* Publish the current chart to context table "CT for test" without loader
```

### 5.5 * Publish the current view to dashboard "dashboardName"
Публикует текущее представление на указанный Дашборд
Можно опубликовать любой объект измерения (справочник, версии, время, выборку кубов), мультикуб, контекстную таблицу и т.д
Шаг включает в себя нажатие на кнопку View и в дропдауне Publish to Dashboard выбирает указанный Дашборд. Проверяет глобальный лоадер
```
* Publish the current view to dashboard "Main Dashboard"
```
Когда лоадер не появляется при публикации используем шаг:
```
* Publish the current view to dashboard "Main Dashboard" without loader
```

### 5.6 * Publish the current view to context table "contextTableName"
Публикует текущее представление на указанную контекстную таблицу
Можно опубликовать любой объект измерения (справочник, версии, время, выборку кубов), мультикуб, кубы и т.д
Шаг включает в себя нажатие на кнопку View и в дропдауне Publish to Context Table выбирает указанную контекстную таблицу. Проверяет глобальный лоадер
```
* Publish the current view to context table "Ввод заявок 2"
```
Когда лоадер не появляется при публикации используем шаг:
```
* Publish the current view to context table "Ввод заявок 2" without loader
```

## 6. Прочие шаги

### 6.1. * Delete view "ViewName"
Удаляет вьюху с именем
```
* Delete view "Test View Tab"
```
 Шаг нажмает на кнопку View > Manage Views, в модальном окне выбирается вьюха и нажимается кнопка Delete и Ok

### 6.2. * Delete "Element"
Удаляет элемент с помощью кнопки Delete на тулбаре
```
* Delete "List 01"
```

### 6.3. * Run action "NameAction"
Запуск скрипта с помощью кнопки Run на тулбаре
```
* Run action "Default Action"
```

### 6.4. * Submit the form
Нажимает на кнопку Submit в модальном окне


[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)
