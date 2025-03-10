# Лабораторная работа IWNO4 Использование контейнеров как среды выполнения

## Цель работы

Данная лабораторная работа призвана напомнить основные команды ОС Debian/Ubuntu. Также она позволит познакомиться с Docker и его основными командами.

## Задание

> Запустить контейнер Ubuntu, установить Web-сервер Apache и вывести в браузере страницу с текстом "Hello, World!".

![run-docker-container](<images/1-run-docker.png>)

> Данная команда запускает контейнер который поднимается с образом ubuntu:latest, так же пробрасывает внешний 8000 порт хоста на внутренний порт контейнера 80

Подробное объяснение команды:

- `docker run` — запускает новый контейнер.

- `-ti` — флаги, означающие запуск в интерактивном режиме с доступом к терминалу.

- `-p 8000:80` — пробрасывает порт 80 контейнера на порт 8000 хоста.

- `--name` containers04 — задает имя контейнеру.

- `ubuntu` — указывает образ, который будет использован.

- `bash` — команда, которая будет выполнена внутри контейнера.

![apt-update](<images/2-apt-update.png>)

`apt update` -  обновляет список доступных пакетов.

`apt install apache2 -y` -
устанавливает веб-сервер Apache без запроса подтверждения.

![apache-install](<images/3-apache-install.png>)

`service apache2 start` - запускает apache.

![apache2-start](<images/4-apache2-start.png>)

### Если сервер работает, в браузере появится стандартная страница Apache

![show-apache-default-page](<images/5-show-apache-default-page.png>)

### Далее я просматриваю содержимое каталога с командой `ls -l /var/www/html`

![var-www-html-directory-contents](<images/6-var-www-html-directory-contents.png>)

### Теперь меняем содержимое **index.html** в **/var/www/html** на `<h1>Hello, world!</h1>`

> `echo '<h1>Hello, World!</h1>' > /var/www/html/index.html` — создаёт HTML-файл с содержимым "Hello, World!".

![index-html-change](<images/7-index-html-change.png>)

### Перезагружаю страницу и вижу результат

![hello-world](<images/8-hello-world.png>)

### Следующим шагом я просматриваю конфигурацию Apache

> Для этого перехожу в каталог конфигурации сайтов `cd /etc/apache2/sites-enabled/`
>
> и вывожу содержимое **000-default.conf** при помощи cat
>
>
> Команда **cat** — это инструмент командной строки, который позволяет создавать файлы, просматривать их содержимое, объединять несколько файлов.

### Получаем следующий дефолтный конфиг для Apache

![apache-000-default-conf](<images/9-apache-000-default-conf.png>)

### Выхожу из контейнера

![exit](<images/10-exit.png>)

### Проверяю список созданных контейнеров

> `docker ps -a` - отображает список всех контейнеров, включая остановленные.

![docker-ps](<images/11-docker-ps.png>)

### Удаляем контейнер при помощи команды docker rm, где rm значит remove

![rm-container](<images/12-rm-container.png>)

## Выводы

В ходе лабораторной работы были освоены базовые команды Docker, установка и настройка Apache в контейнере, а также размещение простой веб-страницы. Работа позволила понять принципы работы контейнеризированных сред и взаимодействие веб-серверов внутри них.

## Репозиторий с выполненной лабораторной

[Repository](https://github.com/ShiroyamaY/usm_containers04)
