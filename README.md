# ЯП - Спринт 15 - Запуск docker-compose проекта API_YAMDB
### Описание

Проект YaMDb собирает отзывы пользователей на произведения. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

### Технологии

* Python 3.7

* Django 2.2

* DRF 

* JWT + Djoser

* Postgresql

* Docker

* NGINX

### Запуск проекта в dev-режиме

- Клонируйте репозиторий и перейдите в него в командной строке.
```bash
git clone git@github.com:Nataliya-miyau/infra_sp2.git
```
- Установите виртуальное окружение c версии Python 3.7 :
```bash
py -3.7 -m venv venv
```
- Активируйте виртуальное окружение :

```bash
source venv/bin/activate
```
- Далее перейдите в директорию api_yamdb и установите зависимости из файла requirements.txt:
```bash
cd api_yamdb

pip install -r requirements.txt
```
- Перейдите в директорию yatube_api и выполните миграции:
```bash
python manage.py makemigrations 

python manage.py migrate
```
- После требуется создать суперпользователя:
```bash
python manage.py createsuperuser
```
- Чтобы запустить проект используйте команду:
```bash
python manage.py runserver
```
### Docker-compose:

- Перейдите в папку с docker-compose:
```bash
cd infra
```
- Запустите контейнеры:
```bash
docker-compose up -d --build 
```
- Выполните миграции:
```bash
docker-compose exec web python manage.py makemigrations

docker-compose exec web python manage.py migrate
```
- Создайте суперпользователя:
```bash
docker-compose exec web python manage.py createsuperuser
```
- Соберите статику:
```bash
docker-compose exec web python manage.py collectstatic --no-input
```
- Создание дамп базы данных:
```bash
docker-compose exec web python manage.py dumpdata > fixtures.json 
```
- Остановка контейнеров:
```bash
docker-compose down -v
```
### Шаблон наполнения env-файла (находится в директории infra)

```bash
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```
### Документация

Документация будет доступна после запуска проекта по адресу /redoc/.

### Автор

[Громова Наталия](https://github.com/Nataliya-miyau) 