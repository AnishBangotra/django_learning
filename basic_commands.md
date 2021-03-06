# basic-django-commands
## Django command line commands as in what you type in the Terminal or Command Prompt` depending on your system have two different syntax operations:

django-admin <command>
django-admin.py <command>
python manage.py <command>

I'm starting with python manage.py <command> syntax for the following...

## 1) python manage.py runserver This command you'll probably run the most of all commands. It means to run a emulated server on your local computer. So, after running it, you can go to [localhost:8000](http://localhost:8000) or [127.0.0.1:8000](http://127.0.0.1:8000).
Requirements: You must run this in the ROOT of yourport django project where manage.py lives.

Useful subcommand: python manage.py runserver <yourport> so you can change the port from above. So python manage.py runserver 8888 would allow you to access django on 127.0.0.1:8888. This is very useful if you want 2 or more Django servers running locally at the same time.

## 2) python manage.py makemigrations
When you make changes to your models, your database needs to understand how these changes might affect the database. This command automatically makes files that document these changes. You can also considers this a version control (aka history) for your Django models. This is useless without ....

## 3) python manage.py migrate This command replaces `python manage.py syncdb` in many ways and the main one being that `migrate` means it will update your database to the latest version of your Django models. `python manage.py migrate` will also insert external packages (such as `django-allauth`) into your database.

## 4) python manage.py collectstatic This command collects your static files to the `STATIC_ROOT` setting. Basically, it brings your `javascript`, `cascading style sheets (css)`, and `images`, to their own hosting server.
The Django developers recommend you use a content delivery network (CDN) for sharing your static files. Here at CFE, we feel the same way. A CDN is a hosting server for your static files.

## 5) python manage.py startapp When you need to add new functionality to your app, this command is your friend. Using it like `python manage.py startapp videos` will automatically create standard files to help you get started on your new app. It's not used as much as #1-4 but still useful.
## Bonus 6) python manage.py startproject This command, is the best of all of them... why? Simply because it starts your Django project so you can use any of the commands above.
