# Basic django ORM/models

## Database model declaration
```python
from django.db import models


class Product(models.Model):
    name = models.CharField(max_length=100, help_text="Name of the product")
    catalog_identification = models.CharField(max_length=8, unique=True, help_text="Unique identification in the catalog")
    
    price = models.FloatField(help_text="Price of the product in euro")
```

### Exercises

* What is the name of the **primary key**?
* What is the type of the **primary key**?
* *Name* and *catalog_identification* are both **CharField**, which is the main difference of these both fields beside of the maximal length? Give an examples what are valid entries.
* In *price* help text a unit is mention, why is this important?
* Can you identify a case, which is allowed by this model but does not make sense in a real world situation?


## Abstract models

```python
from django.db import models


class AbstractCatalogItem(models.Model):
    class Meta:
        abstract = True
    catalog_identification = models.CharField(max_length=8, unique=True, help_text="Unique identification in the catalog")


class Product(AbstractCatalogItem):
    name = models.CharField(max_length=100, help_text="Name of the product")
    
    price = models.FloatField(help_text="Price of the product in euro")


class Inventory(AbstractCatalogItem):
    location = models.CharField(max_length=40, help_text="Location of the inventory item")
```

### Exercise

* 