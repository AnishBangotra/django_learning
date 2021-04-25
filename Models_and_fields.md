# model data types and fields list

### model is the list of database fields it defines. Fields are specified by class attributes. Be careful not to choose field names that conflict with the models API like clean, save, or delete. 

```python
from django.db import models

class Musician(models.Model):
    first_name = models.CharField(max_length=200)
    last_name = models.CharField(max_length=200)
    instrument = models.CharField(max_length=200)

class Album(models.Model):
    artist = models.ForeignKey(Musician, on_delete=models.CASCADE)
    name = models.CharField(max_length=100)
    release_date = models.DateField()
    num_stars = models.IntegerField()
```

### Each field in the model should be an instance of the appropriate Field class. Django uses field class types to determine a few things.
The column type, which tells the database what kind of data to store (e.g. INTEGER, VARCHAR, TEXT).

## Some Basic fields list you need to know
```html
Field Name	
AutoField	
BigAutoField	
BigIntegerField	
BinaryField
BooleanField	
CharField	
DateField	
DecimalField	
DurationField	
EmailField	
FileField	
FloatField	
ImageField	
IntegerField	
NullBooleanField	
PositiveIntegerField
PositiveSmallIntegerField	
SlugField	
SmallIntegerField	
TextField	 
TimeField	
URLField	
UUIDField	
```