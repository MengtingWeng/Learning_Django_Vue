# Learning the Django with python3
![](./image/basic-django.png)

## The useful command
### Start a Django project
```
django-admin startproject <projectName> 
```
### The development server
```
python3 manage.py runserver
python manage.py runserver 8080 //change the port
python manage.py runserver 0:8000 //ip and port
```
### start a new app
```
python manage.py startapp <appName>
```

### check status of ports
```
sudo netstat -lpn |grep :8000
```

### kill process of ports
```
fuser -n tcp -k 8000
or kill <PID>
```
### create the table
The migrate command looks at the INSTALLED_APPS setting and creates any necessary database tables according to the database settings in your mysite/settings.py file.
```
python manage.py migrate
```

### change models and stored as a migration
Migrations are how Django stores changes to your models (and thus your database schema) - they’re just files on disk. 
```
python manage.py makemigrations <appName>
```

### seqmigrate
The sqlmigrate command takes migration names and returns their SQL
```
python manage.py sqlmigrate polls 0001
```

### migrate
run the migrations for you and manage your database schema automatically
```
python manage.py migrate
```

### invoke the Python shell
interact with free Django API
```
python manage.py shell
```

### create an admin user
```
python manage.py createsuperuser
```
### use mysql as database
```
1. pip3 install mysqlclient
2. go to the settings.py file and change the database setting.
'ENGINE': 'django.db.backends.mysq2l',
'NAME': '<MYSQL database name>',
'USER': 'root',
'PASSWORD': '12345',
'HOST': 'localhost'
'PORT': ''
```


