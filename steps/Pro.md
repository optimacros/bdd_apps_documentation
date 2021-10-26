# Pro-шаги (для особых случаев)

# Шаги используемые на Drive Landing

## 1) * Create a new model with name "ModelName"
Создание модели с именем Model 1 находясь в Drive Landing


## 2) * Delete model "ModelName"
Удаление модели в Drive Landing и в нужном месте расположения модели


## 3) * Delete folder "FolderName"
Удаление папки находясь в Drive Landing и в нужной месте расположения модели


## 4) * Rename the model from "ModelName" to "NewModelName"
Переименовываем модель


## 5) * Rename the folder from "FolderName" to "NewFolderName"
Переименовываем папку


## 6) * Copy model "ModelName"
Создание копии модели. В имени скопированной модели будет присутствовать уникальный хэш


## 7) * Press and hold down the mouse button at "Selector" Н
ажать на селектор и не отпускать кнопку мыши (например для группового выделения в связке с шагом ниже)


## 8) * Release the mouse button at "Selector"
Перетаскивание выделения до определенного селектора (например для группового выделения в связке с шагом выше)


## 9) * Compare "Selector" with "File.png"
Шаг для сравнения эталонного скриншота с тем скриншотом который будет делаться при прогоне теста.
Сам шаг довольно специфический. Есть много нюансов, раскажу несколько из них!
Чтобы сделать скриншот эталонный, нужно прогнать сам тест, забрать сделанный скриншот из репорта, положить его в проект в папку screanshots и в следующих запусках теста, шаг уже будет сравнивать один скриншот со вторым.

## 10) * Screenshot page "File.png"


## 11)   * Set "Value" of the cell at the intersection of "CollName" and "RowName" without updating the cell
Выбор из выпадающего списка открывающегося на пересечении колонки и строки без ожидания лоадера и пауз в конце шага.


## 12) * Type "Text" into the cell at the intersection of "CollName" and "RowName" without updating the cell
Прописывает текст на пересечении колонки и строки без ожидания лоадера и пауз в конце шага.


## 13) * Set the cursor position at [Number] in "Selector"
Шаг установит текстовый курсор ввода к указанному по порядку символу в формульной строке


## 14) * Check if the cursor position in "Selector" equals to [Number]
Соотвественно можно проверить с помощью этого шага у какого символа по порядку находится текстовый курсор ввода


## 15)    * Drag "Selector" and set the value equal to [Number]
```* Drag "Zoom Slider" and set the value equal to [1]```
Шаг для увеличения или уменьшения размера приложения в настройках пользователя.


## 16)    * Check if the Grid exists and loaded after [Number] second (s)
Шаг выполняет провергу загрузки грида в течении *** секунд. Если за *** секунд грид не загрузился, то шаг упадет. Выставить мы можем время в пределах 60 секунд


## 17) * Check if the style in "Selector" matches "Style"
```* Check style "heading1" in "Grid Cell(0:13)"```
Проверка стиля в ячейке по координатам


## 18) * Check if the style in "Selector" does not match "Style"
Проверка отсуствия стиля в ячейке по координатам


## 19) * Check if the input value in "Selector" equals to:

```JavaScript 
* Check if the input value in "Formula Input" equals to:
"""
    =	 100+
100+
100
"""
```
Шаг проверяет отступы и текст в инпуте


## 20) * Check if "Selector" title matches:

```JavaScript 
* Check if "Grid Cell(2:1)" title matches:
"""
sdfsdfjsd;lkfjsdlkfjsdlkfj sdfsdfsdfaaaaajkhkjhsdfkljsdhflksdjhfksdljfhksdjfh

sdfsdlkfjsdlkfj lksdjf;sdlkjflkjlksdjf skdfjlsdkfjsd;lfjksdlfj dsfjsdlfkjsdf
"""
```
Шаг проверяет value элементов с отсутпами и всем текстом


## 21) * Check if "Selector" was opened
```* Check if "Grid Context Menu" was opened```
Проверка того что контекстное меню вызванное правой кнопкой мыши по гриду, открылось!
```
* Right click on "Selector"
* Check if "Selector" was opened*
```
Так же можно проверить закрыто ли контекстное меню:

```* Check if "Selector" was closed```


## 22) * Check if CSS style "PropName" of "Selector" equals to [PropValue]
```* Check that "width" of the "GridCell(0:0)" equals to [100px]```
Ширина в px у опредленной колонки. Можно в качестве агрумента передать и другое свойство


## 23) * Check if the grid has right spaces
Проверка того что в конце грида справа есть отступ

## 24) * Check if the grid has down spaces
Проверка того что в конце грида снизу есть отступ


## 25) * Check that elements in the grid are not:
```JavaScript
* Check that elements in the grid are not:
    | 0:-1 | Line Item 1 |
    | 1:-1 | Line Item 2 |
```
Шаг проверит отсуствие элементов в гриде.


## 26) * Check if the elements in context ""DashboardSelector"" grid do not match:
```JavaScript
 * Check if the elements in context "DashboardSelector" grid do not match:
  | 0:-1 | Value | Value | Value |
  | 1:-1 | Value | Value | Value |
```

## 27)   * Check if the height of "Selector" equals to [Number]
``` * Check if the height of "Constraints Formula Line" equals to [213]```
Проверка высоты поля ввода в гриде Optimizer


## 28)    * Clean temp models in current workspace
Очистка временных моделей (копии моделей с хешом и другие модели с хешом)


## 29) * Remove hash from the url
Шаг удалит хэш после id модели

## 30)  * Insert "Text" after hash in the url
 ```* Paste "eyJ0eXBlIjoiTXVsdGljdWJlc0RhdGFCdWlsZGVyVGFiIiwicGFyYW1zIjp7InRpdGxlIjoiTXVsdGljdWJlcyIsImFjdGl2ZVRhYiI6MH19" after hash in the url```
Шаг вставляет дополнительный хеш в адресную строку браузера после ID модели и символа # - Этот шаг нужен для тестирования роутинга
    
    
## 31)   * Set the viewport width to [Pixels], set the height to [Pixels] pixels
Если понадобилось запустить тест с другим размером браузера. Дефолтно запускается с 1920x1080


## 32) * Scroll the vertical scroller to the element "Selector"
Проскролить грид по вертикали к указанному элементу. Грид должен быть прогружен если элемент ниже видимой области..


[Список всех шагов](../steps/allSteps.md)

[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)