# Function Based Views

### Django is based on MVT (Model View Template) architecture and around CRUD (Create, Retrieve, Update, Delete) operations. Generally CRUD means performing Create, Retrieve, Update and Delete operations on a table in a database. 

**Create** – create or add new entries in a table in the database.
**Retrieve** – read, retrieve, search, or view existing entries as a list(List View) or retrieve a particular entry in detail (Detail View)
**Update** – update or edit existing entries in a table in the database
**Delete** – delete, deactivate, or remove existing entries in a table in the database

### You having a project and an app, let’s create a model of which we will be creating instances through our view. In my_app/models.py,
```python
# import the standard Django Model
# from built-in library
from django.db import models
   
# declare a new model with a name "GeeksModel"
class FirstModel(models.Model):
  
    # fields of the model
    title = models.CharField(max_length = 200)
    content = models.TextField()
  
    # renaming the instances of the model
    # with their title name
    def __str__(self):
        return self.title
```

## Now you can go through migrations in order to create Data Base for it
```
Python manage.py makemigrations
Python manage.py migrate
```
 
## Now you can go on creating a django form in your app by naming forms.py

```python
from django import forms
from .models import FirstModel  
# creating a form
class DefaultForm(forms.ModelForm):
  
    # create meta class
    class Meta:
        # specify model to be used
        model = FirstModel
  
        # specify fields to be used
        fields = [
            "title",
            "content",
        ]
```
## Creating view

Create View refers to a view (logic) to create an instance of a table in the database.
In my_app/views.py,
```python
from django.shortcuts import render
  
# relative import of forms
from .models import FirstModel
from .forms import DefaultForm
  
  
def create_view(request):
    # dictionary for initial data with 
    # field names as keys
    context ={}
  
    # add the dictionary during initialization
    form = DefaultForm(request.POST or None)
    if form.is_valid():
        form.save()
          
    context['form']= form
    return render(request, "sample.html", context)

```
### Go on creating this sample.html in a directory name templates/sample.html

```html
<form method="POST" enctype="multipart/form-data">
  
    <!-- Security token -->
    {% csrf_token %}
  
    <!-- Using the formset -->
    {{ form.as_p }}
      
    <input type="submit" value="Submit">
</form>
```

## You can check now your local server for the response!
