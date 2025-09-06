## Бейджик workflow: ##
[![Main Kittygram workflow](https://github.com/Marakes/kittygram_final/actions/workflows/main.yml/badge.svg?branch=main)](https://github.com/Marakes/kittygram_final/actions/workflows/main.yml)


## Summary: ##
    Привет! 
_Данный проект - Cервис для любителей домашних животных. Здесь можете разметить своих роднулек и радоваться этому)_ 

**Проект разработан на Django. Деплой через GitHub Actions в контейнерах Docker.**

**Проект может быть полезен для тех, кто изучает Django, Docker, CI/CD и Postgres или в качестве основы для собственного проекта.**

_Даже имеются необходимые тесты на pytest!!!_

_В общем - пользуйтесь, кому понадобится!)_

---

## Стек технологий: ##

- **Python 3.11+**
- **Django 3.2.3**
- **Django REST Framework 3.12.4**
- **Psycopg2-binary 2.9.3**
- **Djoser 2.1.0**
- **Pytest 6.2.4**

Полный список зависимостей см. в (requirements.txt)

---

## **_Как запустить проект:_** ##

**_Клонировать репозиторий и перейти в него в командной строке:_**

    git clone https://github.com/Marakes/kittygram_final

    cd kittygram_final

## Создать .env файл в корне проекта: ##

    POSTGRES_DB=test_db
    POSTGRES_USER=test_user
    POSTGRES_PASSWORD=test_password
    DB_NAME=test
    DB_HOST=db
    DB_PORT=5432
    
    DEBUG=False
    DJANGO_SECRET=secret_key
    ALLOWED_HOSTS=localhost,127.0.0.1
    SQLITE_ON=False

**_Создать и запустить контейнеры (нужен установленный docker):_**

    docker compose -f docker-compose.production.yml up -d --build

**_Применить миграции и собрать статику:_**

    docker compose -f docker-compose.production.yml exec backend python manage.py migrate

    docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
    

**_Проверить работу:_**

   API: http://127.0.0.1:9000/api/
	
   Админка: http://127.0.0.1:9000/admin/
	
   Фронтенд: http://127.0.0.1:9000

---

### Деплой на сервере (CI/CD): ###

**Используется GitHub Actions, DockerHub, сервер с Docker Compose**

  1) Push в ветку main -> прогоняются тесты
  2) Собираются образы (backend, frontend, gateway)
  3) Пушатся в DockerHub
  4) По ssh разворачиваются на сервере

---




## Автор проекта: ##

Невероятный и непревзойдённый (как и все) студент Яндекс Практикума :)

https://github.com/Marakes

