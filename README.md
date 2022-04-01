# Custom chainable Manager and Queryser
from https://simpleisbetterthancomplex.com/tips/2016/08/16/django-tip-11-custom-manager-with-chainable-querysets.html
```python
class DocumentQuerySet(models.QuerySet):
    def pdfs(self):
        return self.filter(file_type='pdf')

    def smaller_than(self, size):
        return self.filter(size__lt=size)

class DocumentManager(models.Manager):
    def get_queryset(self):
        return DocumentQuerySet(self.model, using=self._db)  # Important!

    def pdfs(self):
        return self.get_queryset().pdfs()

    def smaller_than(self, size):
        return self.get_queryset().smaller_than(size)

class Document(models.Model):
    name = models.CharField(max_length=30)
    size = models.PositiveIntegerField(default=0)
    file_type = models.CharField(max_length=10, blank=True)

    objects = DocumentManager()
```

# django_template
This is a django started template

## Changes
1. Docker dev and prod setup
1. Templates 
1. Bootstrap 5
1. Logging
1. Pipenv for environment
1. .env file
1. Static files 


## Install
1. `git clone https://github.com/almazkun/django_template.git`
2. `pipenv install`
3. `pipenv shell`
4. `python manage.py startapp <app_name>`
5. `python manage.py makemigrations`
6. `python manage.py migrate`
7. `python manage.py runserver`
