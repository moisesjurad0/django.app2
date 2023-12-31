# django.proy2

Django Workshop - 2

## How to begin

can follow this:

- <https://docs.djangoproject.com/en/4.2/contents/>

- <https://www.djangoproject.com/>
  - <https://docs.djangoproject.com/en/4.2/>
    - <https://docs.djangoproject.com/en/4.2/intro/overview/> <= this

- <https://www.djangoproject.com/>
  - <https://www.djangoproject.com/start/>
    - <https://docs.djangoproject.com/en/4.2/intro/tutorial01/> <= or this (i'm using this)

---
<https://docs.djangoproject.com/en/4.2/intro/tutorial01/>

Run:

1. `py -m venv .venv`
    1. `./.venv/Scripts/activate` (in linux)
    1. `./.venv/Scripts/activate.bat` (in windows - CMD) or
    1. `./.venv/Scripts/Activate.ps1` (in windows - PowerShell)
1. `pip install django`
1. `pip install djlint` (for linting)
1. `python -m django --version`
1. `django-admin startproject [proyect_name]` (in this case myWeb1)
1. `cd [proyect_name]` (in this case myWeb1)

verify if works:

1. `python manage.py runserver`

---
Run with docker (continuation from Run steps)

1. add requirements.txt
1. add settings.py support for mysql (include env variables)
1. add Dockerfile
1. add docker-compose.yml
1. add .env files with variables to fill mysql support for db service and web service from docker-compose
1. run `docker-compose --env-file .env up` (or)
1. run `docker-compose up` (to automatically load .env.db and .env.web from docker-compose.yml definition)
1. run `python manage.py migrate` (if using docker or compose or remote db server, use SSH to connect and then run the command)

---
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

<https://docs.djangoproject.com/en/4.2/intro/tutorial02/>

Create Models:

1. add your models in the file polls/models.py
1. add polls app to myWeb1/settings.py
1. run `python manage.py makemigrations polls`
    1. By running makemigrations, you’re telling Django that you’ve made some changes to your models (in this case, you’ve made new ones) and that you’d like the changes to be stored as a migration.

Can review:

1. polls/migrations/0001_initial.py
    1. only open the file to check it
1. python manage.py sqlmigrate polls 0001
    1. this is for review the sql generated

Run the migration:

1. `python manage.py migrate`
1. play with the django shell `python manage.py shell`
    1. add __str__ to models and add items from the django shell

---

Creating an admin user:

1. python manage.py createsuperuser
1. Username: admin
1. Email address: <admin@example.com>
1. Password: **********
1. Password (again): *********

Admin App

1. Login Admin App, go to <http://127.0.0.1:8000/admin/>
1. register models in polls/admin.py¶ (in this case only Question, not Choice, but you could)
1. refresh admin app in <http://127.0.0.1:8000/admin/>
1. verify Question and/or Choice appears under the Polls section (just appearing now)

---

<https://docs.djangoproject.com/es/4.2/intro/tutorial03/>

Add more views:

1. add more views to polls/views.py
1. link those views in polls/polls.urls

Move code from modified index method template for view:

1. create polls/templates/polls/index.html
1. change polls/views.py to send data to the template

use render()

1. use render in index in polls/views.py to shrink

Raising a 404 error

1. update detail method include logic for 404 in polls/views.py
1. add a template for detail method in polls/views.py
1. add the template in polls/templates/polls/detail.html

A shortcut: get_object_or_404()

1. update details method in polls/views.py to shink it
1. update detail template

Removing hardcoded URLs in templates

1. update index.html to get rid of hardcode

Namespacing URL names

1. add app_name var in polls/urls.py
1. add the app_name in the link inside polls/templates/polls/index.html

---

<https://docs.djangoproject.com/en/4.2/intro/tutorial04/>

1. write a form for details view

Use generic views: Less code is better:

1. change and refactor to use generic views

---

<https://docs.djangoproject.com/es/4.2/intro/tutorial05/>

TESTS

1. add a test to pollS/tests.py
1. execute `python manage.py test polls`
1. check the error in django shell
1. fix the error in poll/models.py
1. run the test again `python manage.py test polls` (OK)

more tests

1. add tests to pollS/tests.py

---

<https://docs.djangoproject.com/en/4.2/intro/tutorial06/>

TEMPLATES

---

<https://docs.djangoproject.com/en/4.2/intro/tutorial07/>

admin models

1. 1era version de personalizacion de entidades en el panel de administracion de django (polls/admin.py)

---

<https://docs.djangoproject.com/en/4.2/intro/tutorial08/>

1. `python -m pip install django-debug-toolbar`
1. <https://django-debug-toolbar.readthedocs.io/en/latest/installation.html>

---

<https://docs.djangoproject.com/en/4.2/intro/reusable-apps/>

Advanced tutorial: How to write reusable apps

1. create folder django-polls outside the proyect
1. move polls folders to the newly created folder
1. add LICENSE, MANIFEST.in, pyproject.toml, README.rst, setup.py, setup.cfg (configure Django version, this time 4.2)
1. Try building your package with `python setup.py sdist` (run from inside django-polls). This creates a directory called dist and builds your new package, django-polls-0.1.tar.gz.
1. to install the package: `python -m pip install --user django-polls/dist/django-polls-0.1.tar.gz`
    1. if get "ERROR: Can not perform a '--user' install. User site-packages are not visible in this virtualenv."
        1. <https://bobbyhadz.com/blog/python-error-can-not-perform-user-install>
        1. Open your venv folder.
        1. Click on the pyvenv.cfg file.
        1. Set the include-system-site-packages property to true.
        1. Save the file.
        1. try again
        1. rerun
        1. success
        1. then back to normal
