# Домашнее задание к занятию "`«Оркестрация группой Docker контейнеров на примере Docker Compose»`" 

---

### Задание 1

Сценарий выполнения задачи:
- Установите docker и docker compose plugin на свою linux рабочую станцию или ВМ.
- Зарегистрируйтесь и создайте публичный репозиторий с именем "custom-nginx" на https://hub.docker.com;
- Cкачайте образ nginx:1.21.1;
- Создайте Dockerfile и реализуйте в нем замену дефолтной индекс-страницы(/usr/share/nginx/html/index.html), на файл index.html с содержимым:
```
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I will be DevOps Engineer!</h1>
</body>
</html>

```
- Соберите и отправьте созданный образ в свой dockerhub-репозитории c tag 1.0.0 (ТОЛЬКО ЕСЛИ ЕСТЬ ДОСТУП)
- Предоставьте ответ в виде ссылки на https://hub.docker.com/<username_repo>/custom-nginx/general
 
### Выполнения задания 1

https://hub.docker.com/r/dextron1978/custom-nginx/tags

----

### Задание 2

1) Запустите ваш образ custom-nginx:1.0.0 командой docker run в соответвии с требованиями:
- имя контейнера "ФИО-custom-nginx-t2"
- контейнер работает в фоне
- контейнер опубликован на порту хост системы 127.0.0.1:8080
2) Переименуйте контейнер в "custom-nginx-t2"
3) Выполните команду date +"%d-%m-%Y %T.%N %Z" ; sleep 0.150 ; docker ps ; ss -tlpn | grep 127.0.0.1:8080  ; docker logs custom-nginx-t2 -n1 ; docker exec -it custom-nginx-t2 base64 /usr/share/nginx/html/index.html
4) Убедитесь с помощью curl или веб браузера, что индекс-страница доступна.
В качестве ответа приложите скриншоты консоли, где видно все введенные команды и их вывод.

### Выполнения задания 2

![image.jpg](https://github.com/Byzgaev-I/Docker-Compose/blob/main/2-1.png)

----

### Задание 3

1) Воспользуйтесь docker help или google, чтобы узнать как подключиться к стандартному потоку ввода/вывода/ошибок контейнера "custom-nginx-t2".  
2) Подключитесь к контейнеру и нажмите комбинацию Ctrl-C.  
3) Выполните docker ps -a и объясните своими словами почему контейнер остановился.  
4) Перезапустите контейнер.    
5) Зайдите в интерактивный терминал контейнера "custom-nginx-t2" с оболочкой bash.  
6) Установите любимый текстовый редактор(vim, nano итд) с помощью apt-get.  
7) Отредактируйте файл "/etc/nginx/conf.d/default.conf", заменив порт "listen 80" на "listen 81".  
8) Запомните(!) и выполните команду nginx -s reload, а затем внутри контейнера curl http://127.0.0.1:80 ; curl http://127.0.0.1:81.  
9) Выйдите из контейнера, набрав в консоли exit или Ctrl-D.  
10) Проверьте вывод команд: ss -tlpn | grep 127.0.0.1:8080 , docker port custom-nginx-t2, curl http://127.0.0.1:8080. Кратко объясните суть возникшей проблемы.  
11) Это дополнительное, необязательное задание. Попробуйте самостоятельно исправить конфигурацию контейнера, используя доступные источники в интернете. Не изменяйте конфигурацию nginx и не удаляйте контейнер. Останавливать контейнер можно. пример источника.  
12) Удалите запущенный контейнер "custom-nginx-t2", не останавливая его.(воспользуйтесь --help или google).  

В качестве ответа приложите скриншоты консоли, где видно все введенные команды и их вывод.  

### Выполнения задания 3

Пункт 1-2-3

![image.jpg](https://github.com/Byzgaev-I/Docker-Compose/blob/main/3-1-3.png)

Пункт 4-5-6-7-8

![image.jpg](https://github.com/Byzgaev-I/Docker-Compose/blob/main/3-4-8.png)

Пункт 9-10

![image.jpg](https://github.com/Byzgaev-I/Docker-Compose/blob/main/3-9-10.png)

Пункт 11 (дополнительное задание)

![image.jpg](https://github.com/Byzgaev-I/Docker-Compose/blob/main/3-11.png)

Пункт 12

![image.jpg](https://github.com/Byzgaev-I/Docker-Compose/blob/main/3-12.png)

----

### Задание 4

- Запустите первый контейнер из образа centos c любым тегом в фоновом режиме, подключив папку текущий рабочий каталог $(pwd) на хостовой машине в /data контейнера.  
- Запустите второй контейнер из образа debian в фоновом режиме, подключив текущий рабочий каталог $(pwd) в /data контейнера.  
- Подключитесь к первому контейнеру с помощью docker exec и создайте текстовый файл любого содержания в /data.  
- Добавьте ещё один файл в каталог /data на хостовой машине.  
- Подключитесь во второй контейнер и отобразите листинг и содержание файлов в /data контейнера.  
В качестве ответа приложите скриншоты консоли, где видно все введенные команды и их вывод.

### Выполнения задания 4

![image.jpg](https://github.com/Byzgaev-I/Docker-Compose/blob/main/4.png)

----

### Задание 5

1) Создайте отдельную директорию(например /tmp/netology/docker/task5) и 2 файла внутри него. "compose.yaml" с содержимым:  

```
version: "3"
services:
  portainer:
    image: portainer/portainer-ce:latest
    network_mode: host
    ports:
      - "9000:9000"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock

```

"docker-compose.yaml" с содержимым:

```
version: "3"
services:
  registry:
    image: registry:2
    network_mode: host
    ports:
    - "5000:5000"
```
И выполните команду "docker compose up -d". Какой из файлов был запущен и почему?   

**Выполнения задания 5**





































