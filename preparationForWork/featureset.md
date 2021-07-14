# Создание и настройка файла с расширением .featureset

## Создание файла newDir/test.featureset
Как создавать файлы и папки описано в разделе [Структура файлов и папок](preparationForWork/filesAndFolders.md)

Для того, чтобы сделать новый скрипт активным, необходимо открыть файл-манифест .omapp.json:

```js
{
    "name": "gherkin1",
    "runnableScripts": [
        {
            "id": "f2983d28-2808-4384-93ae-6a4a8ebb7143",
            "path": "all.featureset"
        }
    ],
    "id": "f2983d28-2808-4384-93ae-6a4a8ebb7143"
}
```

И добавить в него строки с расположением нового скрипта и уникальным ID, который можно сгенерировать в Aplication Manager
```js
{
    "name": "gherkin1",
    "runnableScripts": [
        {
            "id": "f2983d28-2808-4384-93ae-6a4a8ebb7143",
            "path": "all.featureset"
        },
        {
            "id": "f2983d28-2808-4384-93ae-6a4a8ebb7143",
            "path": "newDir/test.featureset"
        }
    ],
    "id": "f2983d28-2808-4384-93ae-6a4a8ebb7143"
}
```

## Пример скрипта:
```js
{
  "features": [
    "demo/testDemo.feature"
  ],
  "tags": "(not @bug) and (not @for_future_use) and (not @excluded_from_bdd) and (not @blank) and (not @updateModels) and (not @analitic)",
  "tokens": {
    "default":"default-token",
    "developer": "developer-token",
    "limited": "limited-token",
    "modeller": "modeller-token",
    "notModeller": "notModeller-token"
  },
  "host": "demo.optimacros.com",
  "api": {
    "packageUrl": "http://0.0.0.0:0000/bdd-api.tgz",
    "step_definition": "step_definition-path"
  }
}
```

## Путь к тестам которые будет запускать наш скрипт
```js
{
  "features": [
    "demo/testDemo.feature"
  ],
```
В данном примере указано, что при запуске скрипта запустится файл testDemo.feature, расположенный в папке demo.

Существует несколько вариантов того, как можно указать путь к тестовым сценариям, например:

"demo/.feature" - запускает все файлы с расширением .feature, расположенные в папке demo и дочерних папках.

"demo/testDemo.feature, test1.feature, test2.feature" - запускает файл testDemo.feature, расположенный в папке demo, и файлы test1.feature и test2.feature, расположенные в корне приложения.

"*feature" - запустит все файлы приложения с расширением .feature.

## Теги исключающие запуск тестового сценария
```js
  "tags": "(not @bug) and (not @for_future_use) and (not @excluded_from_bdd) and (not @blank) and (not @updateModels) and (not @analitic)",
```
В данной строке указано, что тестовые сценарии, перед которыми стоит любой из вышеперечисленных тэгов, будут игнорироваться скриптом.
Например, если в файле "demo/testDemo.feature" прописать тэг @bug или @analitic, то все шаги, расположеные после тэга проигнорируются. Если тэг прописать в самом начале тестового сценария, то файл "demo/testDemo.feature" не запустится, даже если явно указать его запуск в скрипте.

## Токены пользователей из под которых запускается тест

```js
  "tokens": {
    "modeller": "modeller-token",
    "notModeller": "notModeller-token"
  },
```
В каждом файле с расширением .feature указывается пользователь, от имени которого будет запускаться тестовый сценарий, а в скрипте .featureset этому имени присваивается токен (28-мизначный код), который можно запросить у администратора проекта.

### Host
```js
  "host": "demo.optimacros.com",
```
Адрес сервера, на котором запустится тестовый сценарий. Естественно у Вас должен быть соответствующий токен.

### BDD API

BDD API - это сборка, в которой находятся шаги и селекторы, специфичные для определенного проекта. Для каждого проекта нужна своя уникальная сборка со своим набором шагов и селекторов.

```js
  "api": {
    "packageUrl": "http://0.0.0.0:0000/bdd-api.tgz",
    "step_definition": "step_definition"
  }
```
#### packageUrl
В строке "packageUrl" указывается адрес архива с необходимой сборкой для данного проекта.

#### step_definition
В строке "step_definition" указывается путь к папке, в которой лежит набор имплементированных шагов.

[Настройка таска в AM и подготовка к работе](../settingsTask.md)

[Оглавление](../README.md)