# Планировщик задач
## Описание

SPA приложение планировщик задач.
Пользователи могут добавлять/удалять/редактировать задачи.

## Технологии

#### Архитектура RESTful API

|Language|Framework|DataBase|WSGI/HTTP Server/Client|Сontainerization|CI/CD|Frontend|
|--------|---------|--------|---------------|----------------|-----|--------|
|Python  |Django   |PostgreSQL  |      Gunicorn| Docker|GitHub Actions| React|
|        |Django REST Framework| |     Nginx|  Docker compose|     |   |
|        |         |           |     Postman|                |     |   |

---


## Установка и запуск проекта:

> _Команды для консоли могут отличаться, данная инструкция адаптирована под OS Windows с использованием командной строки Git Bash._

Для развертывания проекта локально, необходимо предварительно создать директорию для проекта ```taski_project```.

Из локально созданой директории ```taski_project``` необходимо выполнить команду для консоли:
```
git clone https://github.com/MendeIT/taski_project/
```

В корневом репозитории проекта cоздайте файл ```.env``` и наполните данными, как указано в файле ```example.env```.

> _Для запуска приложения необходимо установить Docker. Информацию по установке вы можете найти по ссылке https://www.docker.com/get-started/ ._

После установки Docker измените название образов в docker-compose.yml:
```
...
image: <DockerHub_username>/taski_backend
...
```

Создайте образы, выполнив команду из директории, где расположен docker-compose.yml:
```
docker compose up --build
```

Откройте новый терминал и выполните от имени администратора команды для миграции, сбора статики для контейнера backend:
```
docker compose exec backend python manage.py migrate --noinput
docker compose exec backend python manage.py collectstatic --noinput
docker compose exec backend cp --recursive --update /app/collected_static/. /backend_static/static/
```

Сайт будет доступен: http://localhost:8000

Продуктивной работы!

## Автор
Алдар Дорджиев  
dordzhiev.aldar@yandex.ru