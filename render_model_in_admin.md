# Render model in django admin

### Rendering model in admin refers to adding the model to the admin interface so that data can be manipulated easily using admin interface. This admin interface can be used to manipulate data by performing operations such as INSERT, SEARCH, SELECT, CREATE, etc. as in a normal database. To start entering data in your model and using admin interface , we must specify it in admin.py of your django project file.

### Render Model in Django Admin Interface Explanation
Consider a project named personal having an app named myapp.Now let's create a model

```python
from django.db import models
from django.db.models import Model
# Create your models here.
  
class FirstModel(models.Model):
    title = models.CharField(max_length = 200)
    content = models.TextField(max_length = 200, null = True, blank = True)
    views = models.IntegerField()
    url = models.URLField(max_length = 200)
    image = models.ImageField()
```

### Now if you don't know you must create a superuser to access model through sqlLite django designed gui with command
```python
Python manage.py createsuperuser
```
### Its time to render our model in this admin interface. Go to admin.py in myapp and import the corresponding model from models.py and register it to the admin interface.

```python
from django.contrib import admin
  
# Register your models here.
from .models import FirstModel
  
admin.site.register(FirstModel)
```
## Then just simply check your admin interface by running server, visit http://localhost:8000/admin