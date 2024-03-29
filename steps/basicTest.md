# Описание простого теста

Давайте взглянем на какой-то простой тест:
```js
@testInsert
Feature: UI - Builder Menu - Context Tables - Table - Insert

  Scenario: <Service> I prepare environment
    * Start with an isolated model "E2E Test Model"
    * Start as a "modeller"

  Scenario: <208.1> I can add Context Table in the grid Context Tables "Start" position
    * Click on "Header Menu Element(Context Tables)" in "Header Menu Element(Visualization)"
    * Check if the Grid exists and loaded
    * Insert elements "Context Tables" at position "Start":
      """
      Form 1
      Form 2
      Form 3
      """

    * Check elements in the grid:
      | 0:-1 | Form 1 |
      | 1:-1 | Form 2 |
      | 2:-1 | Form 3 |

  Scenario: <Service>  I destroy environment
    * Delete the current model
```

- В начале мы видим тег @testInsert - он может и не указываться, но если у нас есть много тестов с инсертом элементов где указан этот тег, то мы можем запустить всю группу тестов помеченную этим тегом!

- На второй строчке ```Feature: UI - Builder Menu - Context Tables - Table - Insert``` мы указали место действия или функционал нашего теста.. 

- Далее мы видим первый сервисный сценарий с шагами:
    - ```* Start with an isolated model "E2E Test Model"``` - этот шаг запускает изолированную модель с названием E2E Test Model (т.е. копия модели на момент запуска теста) мы можем не бояться и делать с этой моделью все что заблогороссудится. В конце мы можем удалить эту модель с помощью еще одного сервисного шага    - ```* Delete the current model```

    - ```* Start as a "modeller"``` - Этот шаг указывает под каким пользователем мы хотим запустить наш тест, пользователей мы прописываем в файле [.featureset](preparationForWork/featureset.md)

## Первый пользовательский сценарий
1) Представим что мы хотим в нашем сценарии добавить новые элементы используя кнопку именованный Insert с позицией Start в грид Контекстных таблиц.
Для этого мы используем первый шаг, тот который за пользователя наведет на селектор ``Header Menu(Visualization)`` и после открытия меню найдет и кликнет на пункт ``Context Tables``

   ``` * Click on "Header Menu Element(Context Tables)" in "Header Menu Element(Visualization)"``` - Это комплексный шаг, он включает в себя несколько действий которые описаны чуть выше.

2) После того как мы перешли к гриду с контекстными таблицами, пользователь глазами увидел бы загрузку грида.. и прежде чем он произвел бы какие-то следущие действия, он убедился  и дождался бы загрузки этой страницы. Для этого у нас есть несколько шагов, один из них ```* Check if the Grid exists and loaded```.
Существуют и другие способы убедиться что страница загрузилась - это дождаться проверки како-го нибудь элемента на стринице который присущ именно той табе и гриду, например какая-то колонка или строка в гриде.

3) Далее мы используем следующий комплексный шаг:
```js
    * Insert elements "Context Tables" at position "Start":
      """
      Form 1
      Form 2
      Form 3
      """
```
Этот шаг нажимает на кнопку ``Add Context Tables with Names``, выберет позицию ``Start``, введет в поле название новых элементов и в конце нажмет кнопку `OK`

4)  Шаг по сверению данных в гриде
```js 
    * Check elements in the grid:
      | 0:-1 | Form 1 |
      | 1:-1 | Form 2 |
```
Шаг проверяет существование элементов с позицией строки в первой колонке и названием строки во второй колонке. Конструкция может быть и больше. Мы можем проверять и value клеток. Главное соблюдать правила и синтаксис шага.

5) После всех нужных нам операций мы можем удалить изолированную модель созданную ранее с помощью сервисного сценария:
```js
Scenario: <Service>  I destroy environment
    * Delete the current model
 ```
Если есть необходимость, вы можете не удалять модель и найти эту модель на том воркспейсе на котором запускался тест

[Описание типовых шагов](./prerequisities.md)

[Оглавление](../README.md)