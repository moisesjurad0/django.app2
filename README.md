# django.proy2

Django Proyect 2

## How to begin

can follow this:

- <https://docs.djangoproject.com/en/4.2/contents/>

- <https://www.djangoproject.com/>
  - <https://docs.djangoproject.com/en/4.2/>
    - <https://docs.djangoproject.com/en/4.2/intro/overview/> <= this

- <https://www.djangoproject.com/>
  - <https://www.djangoproject.com/start/>
    - <https://docs.djangoproject.com/en/4.2/intro/tutorial01/> <= or this (i'm using this)

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
1. add settings.py support for mysql (include env variables)
1. add Dockerfile
1. add docker-compose.yml
1. add .env files with variables to fill mysql support for db service and web service from docker-compose
1. run `docker-compose --env-file .env up` (or)
1. run `docker-compose up` (to automatically load .env.db and .env.web from docker-compose.yml definition)
1. run `python manage.py migrate` (if using docker or compose or remote db server, use SSH to connect and then run the command)

creating a new app:

1. `python manage.py startapp polls`
    1. will create new app "polls" and folder structure
1. create new view in views.py in polls
1. create file urls.py and map that view in polls
1. map polls.url in urls.py inside myWeb1

verify if works:

1. open in a browser: <http://localhost:8000/polls/>
1. must see this: "Hello, world. You're at the polls index."

---

Create Models

<https://docs.djangoproject.com/en/4.2/intro/tutorial02/>

1. add your models in the file polls/models.py
1. add polls app to myWeb1/settings.py
1. run `python manage.py makemigrations polls`
