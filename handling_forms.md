# Django Forms

### When one creates a Form class, the most important part is defining the fields of the form. Each field has custom validation logic, along with a few other hooks. This article revolves around various fields one can use in a form along with various features and techniques concerned with Django Forms. Forms are basically used for taking input from the user in some manner and using that information for logical operations on databases. For example, Registering a user by taking input as his name, email, password, etc.

## Syntax:
```python
from django import forms
#Creating a form

class GeekForm(forms.Form):
	title = forms.CharField()
	description = forms.CharField()
```

**Creating a Django Form**

### Creating a form in Django is completely similar to creating a model, one needs to specify what fields would exist in the form and of what type. For example, to input, a registration form one might need first CharField, IntegerField and so on.

### Syntax
```python
from django import forms

class InputForm(forms.Form):
	first_name = forms.CharField(max_length = 100)
	last_name = forms.CharField(max_length = 100)
	age = forms.IntegerField(help_text = "Enter your Age here!")
	email = forms.EmailField(max_length = 50)
	password = forms.CharField(widget = forms.PasswordInput())
```

## Simple to Render Forms

### To render this form into a view, move to views.py and create a home_view as below.

```python
from django.shortcuts import render
from .forms import InputForm

#Create your views here.
def home_view(request):
	context = {}
	context['form'] = InputForm()
	return render(request, 'home.html', context)

#here 'home.html' is an instance to 'form' here created above refrenced by 
#context here.
```

**Create Forms from Models**

### Django ModelForm is a class that is used to directly convert a model into a Django form. If you’re building a database-driven app, chances are you’ll have forms that map closely to Django models.

```python
#import standard django model from built-in library
from django.db import models

class GeeksModel(models.Model):
	#fields of the model are
	title = models.CharField(max_length = 200)
	content = models.TextField()
	last_update = models.DateTimeField(auto_now_add =True)
	media = models.ImageField(upload_to = 'images/')


	def __str__(self):
		return self.title
```

