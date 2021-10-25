


## 3) * Check if "Selector" exists for a long time
* Check if "Card Of Dashboards(Cube МК4 Стандартные заказы и Номенклатура) > Grid Cell(2:1, 99)" exists for a long time
Специфичный шаг, нужный для проверки сущесовования элемента, но с увеличенным таймаутом самого шага. В стандартных шагах заложен таймаут в 60 секунд, по истечению этого времени шаг выдаст ошибку в случае отсуствия проверяемого элемента. Т.е. не дождется элемента и сценарий остановится и продолжится другой сценарий который вероятно тоже упадет так как в предыдущем сценарии не выполнились все заложенные действия


## 4) * Check if "Selector" does not exist for a long time
Шаг по проверке отсуствия элемента с увеличенным таймаутом


## 8) * Check if the value is empty in "Selector"
* Check if the value is empty in "Formula Input"
Проверят что нет никаких данных в инпуте Formula Input



## 7) * Close tab "ModuleName"
Зкарывает указанный таб

## 8) * Wait [Number] seconds
Ожидание в секундах



## 56) * Create a new folder with name "FolderName"
Создание папки находясь в Drive Landing


## 17) * Click using coordinates "X:Y"
> * Right click using coordinates "X:Y"
> * Hover over coordinates "X:Y"

Шаг наведет курсор или кликнет по координатам приложения, если по этой координате будет какой-то элемент, то произойдет какое-то событие. Чаще всего этот шаг применяется для клика по нужному элементу в графике. Дело в том что в графиках тяжело привязаться к элементу и сделать с ним что-то. Ну а к самим настройкам графика мы можем обратиться, многие селекторы уже прописаны. 


## 27)   * Stretch element "Selector" [Pixels] pixels to the "left"
Шаг для растягивания элементов в нужном направлении на нужное колличество px
* Stretch element "Selector" [Pixels] pixels to the "right"
* Stretch element "Selector" [Pixels] pixels to the "top"
* Stretch element "Selector" [Pixels] pixels to the "bottom"


## 16)    * Open the context menu with a hotkey
Вызов диалогового окна по CTRL + Q со списком измерений



# Шаги связанные с буфером

## 46) * Check if the clipboard contains "Text"
> * Check if the clipboard does not contain "Text"

Проверка значений находящихся в буфере обмена или отсуствия значения в буфере

## 47) * Check if the clipboard is empty
Проверка того что буфер обмена пуст

## 48) * Clear Clipboard
Очистка буфера.

## 49) * Copy selection to the clipboard
Шаг копируте в буфер выделенный текст.. 
Вот несколько примеров:
```
* Click on "Row Header(Text col with data)"
* Check if "Selection Row Header(1:-1)" exists
* Copy selection to the clipboard
* Check if the clipboard contains "333"
* Check if the clipboard contains "444"

```

В этом сценарии кликаем на строчку и копируем ее.. выделяются и ячейки этой строки, оттуда и взялись данные в буфере 333 и 444

```
* Click on "Grid Cell(3:0)"
* Press "END" with "SHIFT" and "ALT"
* Copy selection to the clipboard
```

В этом шаге копируются сразу много выделенных ячеек

## 50) * Fill the cells with data from the clipboard
Шаг вставляет данные из буфера в выделенную область.
```
* Click on "Grid Cell(3:0)"
* Click on "Grid Cell(10:5)" while holding "SHIFT"
* Fill the cells with data from the clipboard
```

*Есть еще специфичный похожий шаг:*
> * Fill the cells with data from the clipboard without waiting

Он служит для таких же целей, но без внутренней проверки ожидания.
Применяется в связке с функционалом *Apply By Confirmation (ABC)*

## 51) * Paste from clipboard
Шаг по вставке в выделенную область данных из буфера

## 52) * Copy data from "f:File.csv" to clipboard
Заполняет буфер обмена из csv файла

## 53) * Copy to clipboard:
```JavaScript 
* Copy to clipboard:
    | 100    | 200    | 300    | 400    |
    | Text 1 | Text 2 | Text 3 | Text 4 |
    | 0.1    | 0.2    | 0.3    | 0.4    |
```

Заполняет буфер в виде таблицы из написанного нами контейнера


## 54) * Fill the grid with data from "f:File.csv"

Шаг вставит из csv файла данные в грид от начала координат колонка = 0, строка = 0

Файл импорта должен находиться в папке Fixtures



## 35) * Delete view "ViewName"
Удаление вьюхи, нужно находится в удаляемой вьюхе. Шаг похож на создание вьюхи, так-же нажмет кнопку View > Manage Views, в модалке выберется наша вьюха и нажмется кнопка Delete и Ok

## 35) * Delete "Element"
* Delete "List 01"
Удалить элемент 


## 62) * Run action "NameAction"
Находясь в гриде в котором можно удалить строку, шаг выделит нужный элемент и удалит его через кнопку в тулбаре


## 18)   * Submit the form
Шаг кликает по кнопке Sabmit


[Список всех шагов](../steps/allSteps.md)

[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)