# Начало работы с Gitify

## Установка MODX

### Начало
Для установки Modx нужно запустить следующую команду:

```bash
gitify modx:install [version]
```
Версию необходимо указать в следующем формате:  `2.8.4-pl`

Если версия не указана, по умолчанию будет загружена самая последняя, стабильная версия.

### Параметры установки

После окончания загрузки, необходимо ввести следующие параметры:

* Database Host [`localhost`]
* Database Name [`Folder-name`]
* Database User [`root`]
* Database password
* Database Connection charset [`utf8mb4`]
* Database Charset [`utf8mb4`]
* Database Collation [`utf8mb4_general_ci`]
* Database Prefix [`modx_`]
* Hostname [`Computer-Name`]
---
* Base Url [`/`]
* Manager Language [`en`]
* Manager User [`Folder-name_admin`]
* Manager User Password [`generated`]
* Manager Email
* Core Path [`core/`]
* Manager Directory [`manager/`]: 

## Инициализация репозитория

Сначала инициализируем gitify в папке установки Modx

```bash
gitify init
```

Необходимо ввести следующие параметры:

* Data Directory [`_data/`]
* Backup Directory [`_backup/`]

Необходимо указать, какие именно параметры мы хотим включить в систему git   
Путём ответов [`Y`]es / [`N`]o

* Contexts
* Template Variables
* Content
* Categories
* Templates
* Chunks
* Snippets
* Plugins
* Namespaces, Extension Packages, System Settings
* Form Customization
* Media Sources
* Dashboards
* Currently Installed Packages

Выполняем команду:
```bash
gitify extract
```

После чего мы можем инициализировать репозиторий git 

```bash
git init
touch .gitignore
```

В .gitignore указываем 

```bash
#gitify
_backup/

#Прочее
...
```

Добавляем свои файлы в .gitignore по необходимости и делаем коммит

```bash
git add .
git commit -m "Initial commit"
```

## Алгоритм работы

1. Клонируем репозиторий / Подтягиваем изменения
    ```bash 
    git clone [url] [folder]
    /
    git pull
    ```
1. Вносим изменения в конфиг / Создаём файл конфига.
1. Заносим данные в базу
    ```bash
    gitify package:install --all
    gitify build
    ```
1. Создаём отдельную ветку
    ```bash
    git checkout -b [branch_name]
    ```
1. Вносим правки
1. Сохраняем изменения в файлы
    ```bash
    gitify extract
    ```
1. Делаем коммит и пушим
    ```bash
    git add .
    git commit -m [message]
    git push origin [branch_name]
    ```
1. Создаём мёрдж реквест и просим компетентного сотрудника проверить и сделать мёрдж