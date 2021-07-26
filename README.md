# ML Projects Structure Template

[![v1.0.0](https://img.shields.io/github/manifest-json/v/chegevarae/ml-template?filename=extension%2Fmanifest.json)](https://img.shields.io/github/manifest-json/v/chegevarae/ml-template?filename=extension%2Fmanifest.json) [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)  

**ML Projects Structure Template** - это удобный шаблон для быстрого создания структуры ML-проектов.   

Предлагаемая структура ML-проектов сэкономит время, позволит не потерять результаты каждого эксперимента, включая его метрики (результаты эксперимента) и конфигурацию модели. Это позволит в любой момент обучить модель, показавшую наилучшие метрики, просто взяв сохраненный конфигурационный файл, либо использовать сохраненные веса модели.  

## Структура проекта  

Структура проекта может выглядеть следующим образом:  

ML Projects Structure Template  
|&nbsp;&nbsp;core  
|&nbsp;&nbsp;|&nbsp;&nbsp;project_1  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;predict.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Код для загрузки модели и расчета метрик  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;preprocess.py&nbsp;&nbsp;&nbsp;&nbsp;- Код для препроцессинга и разбиения датасета  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;train.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Код для чтения параметров и обучение модели  
|&nbsp;&nbsp;|&nbsp;&nbsp;project_2  
|&nbsp;&nbsp;|&nbsp;&nbsp;README.md  
|&nbsp;&nbsp;data  
|&nbsp;&nbsp;|&nbsp;&nbsp;processed&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Предобработанные данные  
|&nbsp;&nbsp;|&nbsp;&nbsp;source&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Исходные данные для обработки (.csv файлы)  
|&nbsp;&nbsp;|&nbsp;&nbsp;README.md  
|&nbsp;&nbsp;dev  
|&nbsp;&nbsp;|&nbsp;&nbsp;project_1  
|&nbsp;&nbsp;|&nbsp;&nbsp;exp_1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Папка с результатами 1-го эксперемента  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;config.json&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Содержит все данные для запуска эксперимента  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;logs.md&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Логи, записанные в процессе обучения модели  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;metrics.json&nbsp;&nbsp;&nbsp;&nbsp;- Метрики и путь к данным, на которых они получены  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;model.pth&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Обученная модель машинного обучения  
|&nbsp;&nbsp;|&nbsp;&nbsp;exp_2  
|&nbsp;&nbsp;|&nbsp;&nbsp;predict.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Код для загрузки модели и расчета метрик  
|&nbsp;&nbsp;|&nbsp;&nbsp;preprocess.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Код для препроцессинга и разбиения датасета  
|&nbsp;&nbsp;|&nbsp;&nbsp;train.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Код для чтения параметров и обучение модели  
|&nbsp;&nbsp;|&nbsp;&nbsp;project_2  
|&nbsp;&nbsp;|&nbsp;&nbsp;README.md  
|&nbsp;&nbsp;extension  
|&nbsp;&nbsp;|&nbsp;&nbsp;Changelog_Project_1.md&nbsp;&nbsp;- Changelog 1-го проекта  
|&nbsp;&nbsp;|&nbsp;&nbsp;Changelog_Project_2.md&nbsp;&nbsp;- Changelog 2-го проекта  
|&nbsp;&nbsp;|&nbsp;&nbsp;manifest.json&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Версия и описание для лейбла проекта  
|&nbsp;&nbsp;|&nbsp;&nbsp;README.md  
|&nbsp;&nbsp;images&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Картинки, которые используются в проектах  
|&nbsp;&nbsp;|&nbsp;&nbsp;README.md  
|&nbsp;&nbsp;notebook&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Директория для Jupyter Notebook файлов  
|&nbsp;&nbsp;|&nbsp;&nbsp;project_1  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;project_1_baseline_1.ipynb  
|&nbsp;&nbsp;|&nbsp;&nbsp;|&nbsp;&nbsp;project_1_baseline_2.ipynb  
|&nbsp;&nbsp;|&nbsp;&nbsp;project_2  
|&nbsp;&nbsp;|&nbsp;&nbsp;README.md  
|&nbsp;&nbsp;.gitignore&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Скрытие файлов и папок от системы контроля версий  
|&nbsp;&nbsp;config_sample.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Пример конфигурационного файла для запуска проекта  
|&nbsp;&nbsp;data_connector.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Коннектор к БД для извлечения данных  
|&nbsp;&nbsp;data_preprocessing.py&nbsp;&nbsp;&nbsp;&nbsp;- Библиотека для базовой предобработки данных  
|&nbsp;&nbsp;LICENSE  
|&nbsp;&nbsp;main.py&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Файл для запуска проектов из консоли  
|&nbsp;&nbsp;README.md&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Описание структуры проекта, окружения и информации  
|&nbsp;&nbsp;requirements.txt&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Полный список зависимостей  

Важно организовать код так, чтобы для проведения новых экспериментов требовалось лишь поменять параметры в конфигурационном файле, без изменения кода.  

### core

Папка core содержит основной prod код для работы с проектом. Она включает в себя файлы:  

- train.py — код для чтения параметров и путей из конфигурационного файла, обучение модели с последующей ее сериализацией и сохранением логов;  
- predict.py — код для загрузки модели, расчета метрик на данных и их сохранение;  
- preprocess.py — код для препроцессинга и разбиения датасета, если этого требует задача.  

**Важно!** Если проектов несколько, то каждый набор файлов (проект) должен находиться в своей подпапке данной директории. Управление версиями необходимо осуществлять через функционал Git - репозитория.  

### data

В папке data должны находиться все данные для экспериментов: исходные, обработанные, с добавлением новых признаков и т. д. Для удобства в ней можно создавать подпапки, например, с датами получения данных. При этом все исходные данные помещаются в папку source, а подготовленные для входа в модель в папку processed.  

**source** - исходные данные  
**processed** - подготовленные данные для подачи в модель  

**Важно!** Данную директорию рекомендуется использовать исключительно для небольших файлов, т.е. когда нужно что-то быстро посчитать. Если файл весит больше 2 Мб, то настоятельно рекомендуется положить данные в БД и брать их оттуда.  

### dev

Директория предназначена для проведения экспериментов и подготовки кода для выкатки в прод.  
Для любого изменения в модели, даже одного гиперпараметра, необходимо создавать новую подпапку эксперимента.  

Каждая подпапка exp_n с экспериментом содержит:  

- config.yaml — конфигурационный файл. Может быть в любом структурированном формате, например, JSON или XML, содержит все данные для запуска эксперимента: путь до использованного датасета, гиперпараметры модели, тип обучаемой модели, название и путь для сохранения обученной модели и логов, любые другие параметры для запуска кода.  
- model.pth — обученная модель машинного обучения.  
- metrics.yaml — как и конфигурационный файл, может быть в любом структурированном виде, удобном для команды проекта, хранит метрики модели на путь до датасетов, на которых они были получены, и путь до модели, с помощью которой выполнялись предсказания.  
- logs.md — логи, записанные в процессе обучения модели.  

**Важно!** Если проектов несколько, то каждый набор файлов (проект) должен находиться в своей подпапке данной директории. Управление версиями необходимо осуществлять через функционал Git - репозитория.  

### extension

Директория содержит Changelogs проектов, т.е. после каждого бновления поректа, необходимо вносить в лог все существенные изменения, которые были реализованы.

### images

Директория для картинок, которые используются в проектах.  

### notebooks

Директория для Jupyter Notebook файлов с целью более удобной визуализации и манипуляции с данными, которые удобнее делать в интерактивном режиме. По сути здесь мы реализуем Baseline наших моделей с целью их дальнейшего переноса в dev-папку и последующей доработки в dev для выкатки в прод - core.  

**Важно!** Если проектов несколько, то каждый набор Jupyter Notebook файлов (проект) должен находиться в своей подпапке данной директории и ни в коем случае не использоваться в продакшн. Управление версиями докускается осуществлять через копирование основного файла и присвоение его копии очередного номера версии в формате project_1_baseline_2, при этом в названии файла необходимо избегать пробелов. Управление версиями конкретной baseline модели все же рекомендуется осуществлять через Git - репозиторий.  

## Базы данных проекта

Для работы с ML проектами рекомендуется использовать следующие БД:  

**ClickHouse** - для получения и хранения сырых данных  
**PostgreSQL или MySQL** - для предобработанных данных и подачи их в модель

## Визуализация данных

Для визуализации данных рекомендуется использовать:  

**Superset** - платформа для исследования и визуализации данных (OpenSource)  
**Tableau Desktop** - программное обеспечение для интерактивной визуализации данных и бизнес-аналитики  

