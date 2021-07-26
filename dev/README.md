# Dev — директория с экспериментами

Директория предназначена для проведения экспериментов и подготовки кода для выкатки в прод.  
Для любого изменения в модели, даже одного гиперпараметра, необходимо создавать новую подпапку эксперимента.  

Каждая подпапка exp_n с экспериментом содержит:  

- config.yaml — конфигурационный файл. Может быть в любом структурированном формате, например, JSON или XML, содержит все данные для запуска эксперимента: путь до использованного датасета, гиперпараметры модели, тип обучаемой модели, название и путь для сохранения обученной модели и логов, любые другие параметры для запуска кода.    
- model.pth — обученная модель машинного обучения.  
- metrics.yaml — как и конфигурационный файл, может быть в любом структурированном виде, удобном для команды проекта, хранит метрики модели на путь до датасетов, на которых они были получены, и путь до модели, с помощью которой выполнялись предсказания.  
- logs.md — логи, записанные в процессе обучения модели.  

**Важно! Если проектов несколько, то каждый набор файлов (проект) должен находиться в своей подпапке данной директории. Управление версиями необходимо осуществлять через функционал Git - репозитория.**