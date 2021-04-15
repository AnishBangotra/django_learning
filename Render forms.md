# Render Forms in Django	

## In django forms supports all types of HTML forms and rendering data from them to a view for processing using various logical operations and 
use them to fetch data from the user in a convenient manner.
To begin with forms, one needs to be familiar about GET and POST requests in forms.

## What is HTTP?
HTTP is a set of protocols designed to enable communication between clients and servers. It works as a request-response protocol between a client and server.
A web browser may be the client, and an application on a computer that hosts a web site may be the server.

So, to request a response from the server, there are mainly two methods:

GET : to request data from the server.
POST : to submit data to be processed to the server.

##Let’s create a simple HTML form to show how can you input the data from a user and use it in your view. Enter following code in geeks > templates > home.html

```html
<form action = "" method = "get">
	<label for = "my_name">Anish: </label>
	<input id = "name" type= "text" name = "my_name">
	<input type = "submit">
</form>
```

## Let's render it start by creating a demo view namewhere we need to modify urls.py
```python
from django.urls import path

#importing views from views.py
from .views import demo_view

urlpatterns = [
	path('', home_view),
]
```
## Let’s create a view first and then we will try all methods to fetch data from the form. lets move to our home_view and start checking how are we going to get the data. Entire data from an HTML form in Django is transferred as a JSON object called a request.

```python
from django.shortcuts import render

#Create your views here.
def home_view(request):
	return render(request, "home.html")

```
## Then you can use your local host to render things this way.
GET and POST works in the same way where by default every html form ever written in HTML makes a GET request to the back end of an application, a GET request normally works using queries in the URL.
You can call request.GET or POST, as per need.