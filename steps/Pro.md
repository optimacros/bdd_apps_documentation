# Pro-шаги (для особых случаев)

## 1. Шаги используемые на Drive Landing

### 1.1. * Create a new model with name "ModelName"
Создает модель с именем на странице Drive Landing.
```
* Create new model with a name "New Test Model"
```

### 1.2. * Create a new folder with name "FolderName"
Создает папку с именем на странице Drive Landing.
```
* Create a new folder with a name "New Test Folder"
```

### 1.3. * Delete model "ModelName"
Удаляет модель с именем на странице Drive Landing.
```
* Delete model "New Test Model"
```

### 1.4. * Delete folder "FolderName"
Удаляет папку с именем на странице Drive Landing.
```
* Delete folder "New Test Folder"
```

### 1.5. * Rename the model from "ModelName" to "NewModelName"
Переименовывает модель на странице Drive Landing.
```
* Rename the model from "New Test Model" to "E2E-123"
```

### 1.6. * Rename the folder from "FolderName" to "NewFolderName"
Переименовывает папку на странице Drive Landing.
```
* Rename the folder from "New Test Folder" to "Folder"
```

### 1.7. * Copy model "ModelName"
Создает копию модели на странице Drive Landing.
```
* Copy model "E2E-123" 
```

## 2. Проверка элементов.

### 2.1. * Check if the Grid exists and loaded after [Number] second(s)
Проверяет загрузку грида за определенное время.
```
* Check if the Grid exists and loaded after [1] second
* Check if the Grid exists and loaded after [20] seconds
```

### 2.2. * Check if the style in "Selector" matches "Style"
Проверяет стиль заданной ячейки.
```
* Check if the style in "Grid Cell(0:14)" matches "summary1"
```

### 2.3. * Check if the style in "Selector" does not match "Style"
Проверяет отсутствие стиля заданной ячейки.
```
* Check if the style in "Grid Cell(0:13)" does not match "heading1"
```

### 2.4. * Check if the input value in "Selector" equals to:
Проверяет введенное в поле ввода значение. Проверяет текст и отступы.
```JavaScript 
* Check if the input value in "Formula Input" equals to:
"""
    =	 100+
100+
100
"""
```

### 2.5. * Check if "Selector" title matches:
Проверяет всплывающий текст элемента (Title).
```JavaScript 
* Check if "Grid Cell(2:1)" title matches:
"""
Тут может быть любой длинный текст
перенос строки
        и отступы
"""
```

### 2.6. * Check if "Selector" was opened
Проверяет что контекстное меню открыто.
```
* Check if "Grid Context Menu" was opened
* Check if "Context Menu" was opened
```

### 2.7. * Check if "Selector" was closed
Проверяет что контекстное меню закрыто.
```
* Check if "Grid Context Menu" was closed
* Check if "Context Menu" was closed
```

### 2.8. * Check if CSS style "PropName" of "Selector" equals to [PropValue]
Проверяет CSS свойство элемента (width, height, top, left, color, и др.).
```
* Check that "width" of the "GridCell(0:0)" equals to [100px]
* Check that "background-color" of the "Grid Cell(15:7)" equals to [rgb(249, 126, 87)]
```

### 2.9. * Check if the grid has right spaces
Проверяет что Grid проскролен вправо.

### 2.10. * Check if the grid has down spaces
Проверяет что Grid проскролен вниз.

### 2.11. * Check if the elements in the grid do not match:
Проверяет что Grid не содержит элементы.
```JavaScript
* Check if the elements in the grid do not match:
      | 0:-1 | Реклама ТВ          | 750   | 800   |
      | 1:-1 | Затраты на персонал | 600   | 600   |
```

### 2.12. * Check if the elements in context "DashboardSelector" grid do not match:
Проверяет что Grid в карточке дашборда не содержит элементы.
```JavaScript
* Check if the elements in context "Card of Dashboards(Cube МК1 с Заказами)" grid do not match:
      | 0:-1 | Реклама ТВ          | 750   | 800   |
      | 1:-1 | Затраты на персонал | 600   | 600   |
```

### 2.13. * Check if the cursor position in "Selector" equals to [Number]
Проверяет позицию курсора в инпуте.
```
* Check if the cursor position in "Formula Input" equals to [15]
```

### 2.14. * Check if the height of "Selector" equals to [Number]
Проверяет размер (высоту) элемента.
```
* Check if the height of "Constraints Formula Line" equals to [213]
```

### 2.15. * Compare "Selector" with "File.png"
Сравнивает скриншот элемента с файлом.
```
* Compare "Card Of Dashboards(Cube Заявки)" with "dashboard-screenshot.png"
```
Шаг для сравнения эталонного скриншота с тем скриншотом который будет делаться при прогоне теста.
Сам шаг довольно специфический. Есть много нюансов, раскажу несколько из них!
Чтобы сделать скриншот эталонный, нужно прогнать сам тест, забрать сделанный скриншот из репорта, положить его в проект в папку screanshots и в следующих запусках теста, шаг уже будет сравнивать один скриншот со вторым.


## 3. Действия с элементами.

### 3.1. * Press and hold down the mouse button at "Selector"
Зажимает левую клавишу мыши на элементе.
```
* Press and hold down the mouse button at "Row Header(2:-1)"
```

### 3.2. * Release the mouse button at "Selector"
Наводит курсор на элемент и отпускает зажатую ранее левую клавишу мыши.
```
* Release the mouse button at "Grid Cell(3:4)"
```

### 3.3. * Set "Value" of the cell at the intersection of "CollName" and "RowName" without updating the cell
Установка значения в дропдауне ячейки на пересечении колонки и строки без ожидания изменения значения.
```
* Set "speсialist" of the cell at the intersection of  "User Role" and  "bdd-modeller@optimacros.com" without updating the cell
```

### 3.4. * Type "Text" into the cell at the intersection of "CollName" and "RowName" without updating the cell
Печать в ячейке на пересечении колонки и строки без ожидания изменения значения.
```
* Type "renamed" into the cell at the intersection of  "Code" and  "#5487" without updating the cell
```

### 3.5. * Set the cursor position at [Number] in "Selector"
Устанавливает позицию курсора в инпуте.
```
* Set the cursor position at [15] in "Formula Input"
```

### 3.6. * Drag "Selector" and set the value equal to [Number]
Устанавливает размер приложения в настройках пользователя.
```
* Drag "Zoom Slider" and set the value equal to [1]
```

### 3.7. * Clean temp models in current workspace
Очистка временных моделей на странице Drive Landing.

### 3.8. * Remove hash from the url
Удаляет хэш из url после id модели.

### 3.9. * Insert "Text" after hash in the url
Вставляет дополнительный хеш в адресную строку браузера после ID модели и символа #. Применяется для тестирования роутинга.
```
* Insert "eyJ0eXBlIjoiVmlld1RhYlN0YXRlIiwicGFyYW1zIjp7" after hash in the url
```

### 3.10. * Set the viewport width to [Pixels] and set the height to [Pixels] pixels
Устанавливает размер страницы.
```
* Set viewport width [1366] and height [620] pixels
* Set viewport width [1920] and height [970] pixels
```


[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)
