# User model interaction

## Relation to User model
```python
from django.db import models
from django.contrib.auth import get_user_model


User = get_user_model()


class Product(models.Model):
    name = models.CharField(max_length=100, help_text="Name of the product")
    catalog_identification = models.CharField(
        max_length=8, 
        unique=True, 
        help_text="Unique identification in the catalog"
    )
    
    price = models.FloatField(help_text="Price of the product in euro")

    buyer = models.ManyToManyField(
        User, 
        help_text="Users, who bought this product"
    )
```


### Exercise

* From which location comes **User**?
* Is it possible to determine (based on this model), how often a **User** bought a **Product**?