# CI и CD проекта api_yamdb

![example workflow](https://github.com/apolwow/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

#### Описание
Проект реализует REST API для работы с отзывами на различные произведения искусства.
Он представлен в виде web-приложения и базы данных, поднятых в docker-контейнерах.
API позволяет:

* 	регистрировать пользователя с различными ролями (пользователь, модератор, администратор)
* 	выполнять аутентификацию с помощью JWT
* 	просматривать, создавать, редактировать и удалять произведения
* 	просматривать, создавать и удалять жанры и категории произведений
* 	просматривать, создавать, редактировать и удалять отзывы на произведения
* 	просматривать, создавать, редактировать и удалять комментарии к отзывам
* 	просматривать, создавать, редактировать и удалять пользователей (администратор)

Проект доступен по адресу http://51.250.18.97

#### Шаблон наполнения env-файла

```
DB_ENGINE=<...> # указываем, что работаем с postgresql
DB_NAME=<...> # имя базы данных
POSTGRES_USER=<...> # логин для подключения к базе данных
POSTGRES_PASSWORD=<...> # пароль для подключения к БД (установите свой)
DB_HOST=<...> # название сервиса (контейнера)
DB_PORT=<...> # порт для подключения к БД
SECRET_KEY=<...>	# ключ для settings.py
```

#### Как запустить проект
Клонировать репозиторий и перейти в него в командной строке:

`https://github.com/apolwow/infra_sp2.git`

Перейти в директорию с файлом docker-compose.yaml:

`cd /infra`

Собрать контейнеры и запустить их:

`docker-compose up -d --build`

Выполнить миграции, создать суперпользователя и собрать статику, выполнив поочередно команды:

```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

Команда для заполнения базы данными:

`docker-compose exec web python manage.py loaddata fixtures.json`

#### Остановка проекта
Остановить контейнеры, с последующим их удалением:

`docker-compose down -v`

#### Основные использованные технологии

- [Python](https://www.python.org/) - язык программирования.
- [Django](https://www.djangoproject.com/) - свободный фреймворк для веб-приложений на языке Python.
- [Django REST Framework](https://www.django-rest-framework.org/) - мощный и гибкий набор инструментов для создания веб-API.
- [Simple JWT](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/) - плагин аутентификации JSON Web Token для Django REST Framework.
- [Docker](https://docs.docker.com/) - официальная документация Docker
- [Dockerfile](https://docs.docker.com/engine/reference/builder/) - официальная документация Dockerfile
- [Docker Compose](https://docs.docker.com/compose/) - официальная документация Docker Compose
- [YamDB](https://hub.docker.com/repository/docker/apolwow/yamdb_final) - образ yamdb.
- [PostgreSQL](https://hub.docker.com/_/postgres) — объектно-реляционная система управления базами данных (СУБД)
- [Nginx](https://hub.docker.com/_/nginx) — веб-сервер

#### Автор

- [Aleksey Polozhentsev](https://github.com/apolwow)

#### Лицензии

- Этот проект использует [MIT License](https://opensource.org/licenses/MIT)