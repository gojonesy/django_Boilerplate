Welcome to the Django Boilerplate Instructions
==============================================

This contains our best-practices layout and functionality for **Django Projects**.

It enables us to start a *complex* Django Project quickly and with few setup headaches.

Some Functionality:

- **different virtual environments** for developing, testing and production
- Project Structure
- **HTML5 boilerplate**
- Template inheritance
- Functional **tests**
- robots.txt and humans.txt configured
  
This is all based upon the fantastic **step by step** [taskbuster tutorial](http://marinamele.com/taskbuster-django-tutorial) . 

To setup and start using, first look at requirements and then check out the quick_start .



Requirements
============

Necessary requirements for this Django Project Boilerplate are:

- **python3** and **pip3**
- **virtualenv and virtualenvwrapper**
- **Firefox** (to use Selenium's Webdriver in functional tests)
  

Download Firefox from the official [website](https://www.mozilla.org) . 


Quick start
===========

Create a Development Environment
--------------------------------

    mkvirtualenv <project_name>_dev


Install Django
--------------

    pip install django


Start a Django Project using this template
------------------------------------------

    django-admin.py startproject --template=https://github.com/gojonesy/django_boilerplate/zipball/master --extension py,md,rst,txt project_name .


Secret Django Key
-----------------

There is no **SECRET_KEY** setting in any of the settings files.

You can generate a [SECRET_KEY](http://www.miniwebtool.com/django-secret-key-generator) .


Project Name
------------

This project is named *django_boilerplate_project*, when you base a project on this boilerplate, the project name should be changed by the download. However, you should verify that the project name is correct in a few places:

- *django_boilerplate_project* **folder** (the top project folder)
- *django_boilerplate_project*/django_boilerplate* **folder** (the project name)


Virtual environments and Settings files
---------------------------------------

Create a development environment.::

    > mkvirtualenv <project_name>_dev


Edit the activate.bat file: ::

    C:\users\username\Envs\<project_name>_dev

Add the lines: ::

    SET DJANGO_SETTINGS_MODULE=<project_name>.settings.dev
    SET SECRET_KEY="your_secret_key"

Generate a [SECRET_KEY](http://www.miniwebtool.com/django-secret-key-generator)


And then in the deactivate.bat file: ::
    
    SET DJANGO_SETTINGS_MODULE=
    SET SECRET_KEY=


Repeat all of these steps for the test environment: ::

    > mkvirtualenv <project_name>_test
    > C:\users\username\Envs\<project_name>_test

    SET DJANGO_SETTINGS_MODULE=<project_name>.settings.test
    SET SECRET_KEY="your_secret_key"


Now, install all packages that you have setup in your requirements in each environment::

    > workon <project_name>_dev
    > pip install -r requirements/dev.txt
    > workon <project_name>_test
    > pip install -r requirements/test.txt


Static Files
------------

Download the latest [HMTL5 Boilerplate](https://html5boilerplate.com/)

Download the latest [Bootstrap](http://getbootstrap.com/getting-started/#download).

Download Compressed [Jquery](http://jquery.com/download/).

Move templates around::
    
    >mv index.html, 404.html, humans.txt, robots.txt to <project_name>/templates
    >mv index.htmal base.html


Move all other downloaded files to Static::
    
    >mv HTML5BP Bootstrap Jquery <project_name>/static/


Install and configure PostgreSQL
--------------------------------
    
Download [PostgreSQL](https://www.postgresql.org/download/windows/).


After it is installed, add it to the system path: ::
    
    C:\Program Files\PostgreSQL\9.6\bin

Open a command prompt: ::
    
    > pg_config
    > psql -h localhost
    > \q

    > createdb <project_name>_db
    > psql
    > CREATE ROLE <project_name>_user WITH LOGIN PASSWORD 'mypassword';
    > GRANT ALL PRIVILEGES ON DATABASE <project_Name>_db TO <project_name>_user;
    > ALTER USER  <project_name>_user CREATEDB;

    > pip install psycopg2

Edit the ENV activate.bat files and add: ::

    set DATABASE_NAME=<project_name>_db
    set DATABASE_USER=<project_name>_user
    set DATABASE_PASSWORD=mypassword


Migrate the changes: ::

    manage.py check
    manage.py migrate
    manage.py createsuperuser
