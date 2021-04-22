# Using Django Templates

## Mostly in django template is  a directory containing files in HTML, CSS and Javascript in an .html file. Django framework efficiently handles and generates dynamically HTML web pages that are visible to end-user. Django mainly functions with a backend so, in order to provide frontend and provide a layout to our website, we use templates.

## Django templates can be used to show your static data on your backend as well as your database and APP_DIRS, you can check your default settings.py on your django app, it can also fetch data form different databases connected to the application through a context dictionary.

## Example:
## Creating a info view with some data later which fetched by an html django template.

```python
from django.shortcuts import render

#fucntion
def default_view(request):
	#creating a dictionary
	context = {
		"title": "Numbers",
		"values": [1,2,3,4,5,6,7,8,9,10]
	}
	#now render this with an template 
	return render(request, "def_temp.html", context)
```
## Creating a url to render this view, 
```python
from django.urls import path

#importing view
from .views import default_view

url_patterns = [
	path('', default_view),
]
```
## Now lets create this (def_temp)
```HTML
<!DOCTYPE html>
<html lang="en"> 
<head> 
    <meta charset="UTF-8"> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <meta http-equiv="X-UA-Compatible" content="ie=edge"> 
    <title>Homepage</title> 
</head> 
<body> 
    <h1>Fetching data</h1> 
    <p> Data  are {{  title }}</p>
    <h4>Values are </h4>
    <ul>
    {% for i in values %}
    <li>{{ i }}</li>
    {% endfor %}
    </ul>
</body> 
</html> 
```

## Variables

##Variables outputs a value from the context, which is a dict-like object mapping keys to values. The context object we sent from the view can be accesses in template using variables of Django Template.

## Syntax
## {{ variable_name }}