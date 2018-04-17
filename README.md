# Learning_Django_Vue

* Do not forget to add this line into the setting file. Otherwise, we can not find the template files.
```
INSTALLED_APPS = [
    'journal.apps.JournalConfig',


TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'template')],
```