* pip install django
* pip install djangorestframework
* pip install psycopg2-binary


* comment out DATABASES in settings.py, add:
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "postgres",
        "USER": "postgres",
        "PASSWORD": "postgres",
        "HOST": "db",
        "PORT": 5432,
    }
}
* add this to docker-compose.yml:
db:
    image: postgres
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
* `docker compose up`
* `docker-compose run web python manage.py migrate`
* `docker-compose run web bash` -> takes you container terminal
  * python manage.py createsuperuser
  * exit container terminal with `exit`