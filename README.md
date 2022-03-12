![example workflow](https://github.com/EvgenyAlexandrov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
## Проект api_yamdb
### Описание
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Title). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен.
### Установка Docker:
Зайдите на [официальный сайт проекта](https://www.docker.com/products/docker-desktop) и скачайте установочный файл Docker Desktop для вашей операционной системы.
### Запуск проекта в dev-режиме
- Клонировать репозиторий и перейти в него в командной строке:
```
$ git clone https://github.com/EvgenyAlexandrov/infra_sp2.git
```
- Создайте файл .env с переменными окружения для работы с базой данных:
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```
- Команды для Docker:
Поднятие и создание контейнеров
```
docker-compose up -d --build
```
Выполнение миграций:
```
docker-compose exec web python manage.py makemigrations reviews
docker-compose exec web python manage.py migrate
```
Создание суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
Подключение статики:
```
docker-compose exec web python manage.py collectstatic --no-input
```
Создание дамп (резервная копия) базы:
```
docker-compose exec web python manage.py dumpdata > fixtures.json
```
Остановка и удаление контейнеров:
```
docker-compose down -v
```
### Технологии
Python 3.7, Django 2.2, DRF, JWT, Docker
### Автор
[Евгений Александров](https://github.com/EvgenyAlexandrov)
