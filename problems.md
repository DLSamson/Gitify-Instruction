# Возможные проблемы

## Access denied on backup / Откзано в доступе при бэкапе

При вызове команды:     
`gitify backup`

Нам может быть отказано в доступе.

Возможные решения:
* Вызывать команду с опцией `-ntbs`, `--no-tablespaces`
* В файле `Gitify/src/Command/BackupCommand`, на строке 130 заменить 
    ```php
    if ($database_password != '') {
        $password_parameter = "-p{$database_password}";
    }
    ```
    на 
    ```php
    if ($database_password != '') {
        $password_parameter = "--password={$database_password}";
    }
    ```

## Таблица не найдена / Table not found

При вызове команды:     
`gitify backup`

Вероятно, вы уже попытались изменить параметры команды В файле `Gitify/src/Command/BackupCommand` на строке 136

Предположительно, дело в:
- Параметры интерпретируются в неверном порядке
- Имя/Пароль/База имею одно значение (Упрощение для локальной разработки)

## Пакет уже установлен / Package is already installed

При вызове команды      
`gitify package:install --local`

Package `<name>` is already installed.

Но в админке он не установлен. 

Вероятно, об установке есть записи в базе данных.
Это бывает, если вручную удалить какие-то модули

Решение:
* Удалить записи о пакетах в базе данных в табличке: `modx_transport_packages`
* Установить пакеты вручную, через поиск локальных траспортных пакетов

## Невозможно загрузить класс Provider для установки / Cannot load Provider to install

При вызове команды      
`gitify package:install`

Решение: 
* Конкретизировать установку c `--all`, `--local`