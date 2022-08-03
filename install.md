# Установка Gitify

## Установка через Composer

```bash
composer global require modmore/gitify:^2
```

## Установка через Git

Копируем репозиторий в любую удобную папку

```bash
git clone https://github.com/modmore/Gitify.git Gitify
cd Gitify
composer install
chmod +x bin/gitify
```

## Глобальный доступ

Для глобального доступа необходимо прописать путь до исполняемого файлы в переменную среды

Открываем свойства системы и нажимаем на переменные окружения:

![Свойства системы](./images/install/system_properies.png)

В списке выбираем Path и нажимаем изменить:

![Переменные окружения](./images/install/env_vars.png)

Нажимаем кнопку создать, в новое поле вставляем путь до папки, куда произвели `git clone` + \bin, в котором лежит файл gitify

![Изменение переменной](./images/install/change_var.png)

Нажимаем ОК на каждое окно и перезапускаем консоль