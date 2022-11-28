# Technologies:
- Python
- Django
- Django REST Framework
- PostgreSQL
- Docker
- Swagger
- GitHub Actions

# Docker:
docker build .
docker-compose build

docker-compose run --rm app sh -c "flake8"
docker-compose run --rm app sh -c "django-admin startproject app ."
docker-compose run --rm app sh -c "python manage.py startapp core"

# Run configured command:
docker-compose up


# Testing with Django -> Django test framework - based on unittest library
python manage.py test

docker-compose run --rm app sh -c "python manage.py test"

- mocking

Testing APIs -> Django REST Framework API Client

# Database
- psycopq2 - most popular PostgreSQL adaptor for python
			- has some dependencies (C compiler, python3-dev, libpq-dev)

docker-compose down
docker-compose build
docker-compose up

Fixing database race dondition -> wait_for_db command




docker-compose run --rm app sh -c "python manage.py startapp core"
docker-compose run --rm app sh -c "python manage.py test"

docker-compose run --rm app sh -c "python manage.py wait_for_db"


Clear volume:
docker volume ls
docker volume rm recipe-app-api_dev-db-data


### API Documentation (drf-spectacular + swagger) - OpenAPI

1.Add drf-spectabular to req.txt
2.Add rest_framework and drf-spectacular to settings. Add also:
REST_FRAMEWORK = {
    'DEFAULT_SCHEMA_CLASS': 'drf_spectacular.openapi.AutoSchema',
}

docker-compose build
docker-compose up
docker-compose run --rm app sh -c "python manage.py startapp user"
docker-compose run --rm app sh -c "python manage.py test"


PATCH - only change user name
PUT- change everything

### Recipe image API
1.add dependencies
Dockerfile: jpeg-dev

STATIC VS MEDIA

Gather all static files:
python manage.py collectstatic

### Deployment
docker build . -> use this when there is not docker-compose, only Dockerfile

dcoker-compose -f docker-compose.yml up

dcoker-compose -f docker-compose.yml up -d (run in deamon mode)
docker-compose -f docker-compose.yml logs