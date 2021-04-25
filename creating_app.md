# Create an App in Django :

### To create a basic app in your Django project you need to go to the directory containing manage.py and from there enter the command line: 
```python
python manage.py startapp FrstApp
     
```
### Now to create a basic app in your Django project you need to go to the directory containing manage.py and from there enter this command 
```python
django-admin startapp FrstApp
```
### Now you can see your app directory created.

## Pre-installed apps in django – 
### Django provides some pre-installed apps for users. To see pre-installed apps go checkout your app settings.py file, you will find INSTALLED_APPS. Apps listed in INSTALLED_APPS provided by django to done backend process with ease.

### Now go on and simply add your app within installed_apps

```python
INSTALLED_APPS = [
	'django.contrib.admin',
	'django.contrib.auth',
	'django.contrib.contenttypes',
	'django.contrib.sessions',
	'django.contrib.messages',
	'django.contrib.staticfiles',
	'FrstApp',
]
```
### Now as we are done with creating of the app, only thing left is to render this app using URL's we need to include the app in our main project so that URLs redirected to that app can be rendered.
```python
from django.contrib import admin
from django.urls import path, include
 
urlpatterns = [
    path('admin/', admin.site.urls),
    # Enter the app name in following
    # syntax for this to work
    path('', include("FrstApp.urls")),
]
```

## Now you are ready to go creaing models, views and urls it will work totally fine.