
# Основные сценарии использования Diplodoc
## Создание простого документационного проекта в YFM 


### Структура проекта
Базовый проект состоит из нескольких конфигурационных файлов и страниц с контентом, связанных между собой в следующую структуру: 


```
input-folder
|-- .yfm (Файл конфигурации)
|-- toc.yaml (Оглавление)
|-- presets.yaml (Пресеты переменных)
|-- index.yaml (Разводящая страница)
|-- pages (Файлы с контентом)
    |-- faq.md
    |-- how-to.md
|-- _assets (Каталог с изображениями)
    |-- image1.png
    |-- image2.png
|-- _includes (Каталог с файлами для переиспользования)
    |-- faq_shared_block.md
```


Больше информации про параметры и конфигурацию можно найти по [ссылке](./project/index.md). 



### Сборка проекта 
Сборка выполняется с помощью инструмента Builder в командной строке.



Чтобы запустить сборку, выполните команду, указав обязательные ключи запуска


-  input, -i — путь до директории проекта.


- output, -o — путь до директории, предназначенной для выходных данных (статических HTML).


#### Пример
```
yfm -i ./input-folder -o ./ouput-folder
```


### Результат 
После успешного выполнения работы сборщика появляется  или готовый проект HTML или проект в YFM.
Часто вывод в YFM применяется для создания подразделов и включения в крупные проекты. 



### Использование 
Готовые проекты в HTML можно использовать локально или разместить на подходящем для Вас хостинге, включая S3-like хранилище.



## Интеграция в Ваш процесс разработки  
### Создание и построение проекта 

В общем случае структура проекта и процедуры построения не отличаются от описанного в предыдущей секции. 
Однако в случае интеграции с Вашими СI/CD пайплайнами требуется включение Builder для срабатывания по триггерам обновления документации в репозитории. 

Если при коммите в проекты, написанные на С++ или Java пайплайны вызывают определенные компиляторы, то для документации в таком случае 
роль “компилятор” берет на себя Builder. C его помощью генерируются артефакты, которые могут быть автоматически выложены на 
внутренние или внешние ресурсы для доступа конечных пользователей. 

### Подключение плагинов и расширенная конфигурация
Как правило, большие документационные проекты используют дополнительные возможности по работе с контентом и специфичные конфигурации для построения. 
Примером таких расширений является возможность работы с видео или многострочных таблиц.
Подробнее о способах корректного отображения и трансформации контента можно почитать на [странице](./plugins/index.md).

Особенностью конфигурации при построении может быть возможность отключения линтера или сборка проекта в виде одного большого html файла.
Дополнительно о таких возможностях можно ознакомиться на [странице](./tools/transform/settings.md).



## Работа с Github и публикация документов на своем домене или домене https://diplodoc.com 

Если Ваш проект использует Github как систему контроля версий и место хранения исходного кода Вашей документации, Diplodoc позволит создать полностью интегрированный пайплайн работы, покрывающий все шаги от внесения изменений в исходные тексты до построения проекта с помощью Github actions и интеграции с Elastic Search. 

[Свяжитесь с нами](https://diplodoc.com/#contact), чтобы обсудить детали Вашей конфигурации и возможные варианты решения. 