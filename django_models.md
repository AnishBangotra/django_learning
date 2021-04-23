# Django Models

## Models in django uses to create like tables, fields which basically is the SQL of database one uses with django.SQL contains lot of different queries for creating, deleting, updating database.

### Where this model which represents data field automatically gives you database access by generating access API 

```python
from django.db import models

#Creating model
class defModel(models.Model):
	title = models.CharField(max_length = 200)
	content = models.TextField()
```
### Here we are using django database model subclass django.db.models.Model

### Now create any app within your project and modify its models.py by adding a new model like this.

```python
# import the standard Django Model
# from built-in library
from django.db import models
  
# declare a new model with a name "NewModel"
class NewModel(models.Model):
        # fields of the model
    title = models.CharField(max_length = 200)
    content = models.TextField()
    last_modified = models.DateTimeField(auto_now_add = True)
    img = models.ImageField(upload_to = "images/")
  
        # renames the instances of the model
        # with their title name here
    def __str__(self):
        return self.title
```

### Whenever we create a Model, Delete a Model, or update anything in any of models.py of our project. We need to run two commands makemigrations and migrate. makemigrations basically generates the SQL commands for preinstalled apps (which can be viewed in installed apps in settings.py) and your newly created app’s model which you add in installed apps whereas migrate executes those SQL commands in the database file.

## Commands
```html
Python manage.py makemigrations

Python manage.py migrate
```

### Now the only thing left is to render these models which done by the django admin interface of your app in admin.py. Simply import your model and register it to your admin interface.

```python
from django.contrib import admin 
    
# Register your models here. 
from .models import NewModel
    
admin.site.register(NewModel) 
```
