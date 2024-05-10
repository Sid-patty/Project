Run Folowing Commands : 

1. pip install django
    
Setting up Virtual env, Optional if not asked in question : 
a. python -m venv myenv
b. myenv\Scripts\activate

2. django-admin startproject project_name
3. cd project_name
4. python manage.py makemigrations
5. python manage.py migrate
6. python manage.py startapp app_name
7. Add app_name in project_name > settings.py > INSTALLED_APPS list
8. Make urls.py in app_name directory
9. Open urls.py of project_name and add your url in urlpatterns list, example
    path('?', include("app_name.urls"))  
    (Add any prefix you want in place of '?', Example: "api/" or "")
10. python manage.py runserver 

myapp urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
    # Add more URL patterns here
]


9. myfirst urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),  # Add this line
]

views.py
from django.shortcuts import render
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, this is the index page of my app.")