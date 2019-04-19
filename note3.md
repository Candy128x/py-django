## Commands

- To create a project
=> django-admin startproject project_name
Eg: E:\4-Data\python\django\firstproject>django-admin startproject firstproject

- To enable django project on local system
=> python manage.py runserver
- Hit: http://127.0.0.1:8000/ OR localhost:8000 in browser


### Apply all migrations: admin, auth, contenttypes, sessions
- Technically this warning doesn’t matter at this point. Django is complaining that we have not yet “migrated” or configured our initial database. Since we won’t actually use a database in this chapter, the warning won’t affect the end result.
- However since warnings are still annoying to see, we can remove it by first stopping the local server Control+c and the running the command python manage.py migrate.
=> python manage.py migrate
Eg: E:\4-Data\python\django\firstproject\firstproject>python manage.py migrate


- To create app 
- Go in project_name dir
=> cd project_name
Eg: cd firstproject
- To create django app
=> python manage.py startapp app_name
Eg: E:\4-Data\python\django\firstproject\firstproject>python manage.py startapp firstapp


---
# Print `Hello World :]` in django

1)
- firstproject/firstproject/setting.py
- Add: 'firstproject' in INSTALLED_APPS section

2)
- In firstprojects/firstapp/views.py
- Wrote code

```
from django.shortcuts import render
from django.http import HttpResponse

def homePageView(request):
    return HttpResponse('<h1>Hello World :]</h1>')

```

3)
- Create urls.py file in firstproject/firstapp/
- Wrote code..

```
from django.urls import path
from .views import homePageView

urlpatterns = [
    path('', homePageView, name='home')
]

```

4) 
- In firstproject/firstproject/urls.py
- Modify code..

```
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('firstapp.urls')),
]

```
