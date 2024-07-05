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
