# django.proy2

Django Proyect 2

## How to begin

can follow this: <https://docs.djangoproject.com/en/4.2/intro/tutorial01/>

or

Run:

1. `py -m venv .venv`
    1. `./.venv/Scripts/activate` (in linux)
    1. `./.venv/Scripts/activate.bat` (in windows - CMD) or
    1. `./.venv/Scripts/Activate.ps1` (in windows - PowerShell)
1. `pip install django`
1. `python -m django --version`
1. `django-admin startproject [proyect_name]` (in this case myWeb1)
1. `cd [proyect_name]` (in this case myWeb1)

verify if works:

1. `python manage.py runserver`

Run with docker (continuation from Run steps)

1. add requirements.txt
1. add settings.py support for mysql
1. add .env file with variables to fill previous step
1. add Dockerfile
1. add docker-compose.yml
1. docker-compose --env-file .env up
