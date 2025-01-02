
# Classes

## Writing class practices

The exercises this time have 
### Exercise
* Write a class, which can fulfill the following code
* Can the code handle other values than 'hello'?
```python
from abc.collection import Callable

# Provided code
def prepare_function(return_value: str) -> Callable:
    def return_str() -> str:
        return return_value
    return return_str


hello = prepare_function('hello')

# 'Prox' is to implement
proxy = Proxy(func=hello)
assert proxy.delay() == 'delay\nhello'

assert proxy() == 'hello'
```
**Hint:** For the last call you might want to search for dunder methods.


```python
# assuming, we can get the consumed electricity from an electric meter
# via an HTTP request (endpoint '/consumption/current/')

# electric_meter1 has a current consumption of 24
electric_meter1 = ElectricMeter('https://my_electric_meter1.th')
# electric_meter2 has a current consumption of 42
electric_meter2 = ElectricMeter('my_electric_meter2.th')
# electric_meter2 has a current consumption of 42
electric_meter3 = ElectricMeter('my_electric_meter2.th')
# for simplification, a dict can be used to map the URL to current consumption

assert electric_meter1.get_url() == 'https://my_electric_meter1.th'
assert electric_meter2.get_url() == 'https://my_electric_meter2.th'
assert electric_meter1.get_current_consumption() == 24
assert electric_meter2.get_current_consumption() == 42

if electric_meter1 != electric_meter2:
    total_consumption: float = electric_meter1 + electric_meter2
    assert total_consumption == 66

assert electric_meter2 == electric_meter3
```


### Special questions

* What kind of approach is such a way of starting an implementation?
* In the proxy example a function returns a function. In which construct is this extremely common?

## Inheritance

```python
class Product:
    
    name: str
    price: float
    
    def __init__(self, name: str, price: float):
        self.name = name
        self.price = price


class Bread(Product):
    
    def __str__(self):
        return f'Bread: {self.name}'


class Milk(Product):
    
    def __str__(self):
        return f'Milk: {self.name}'


class ShoppingCart:
    
    product_list: dict
    
    def __init__(self):
        self.product_list = {}
        

baguette = Bread('baguette', 2.69)
toast = Bread('Toast', 1.99)
milk = Milk('full', 0.99)

shopping_cart = ShoppingCart()
shopping_cart.add_product(toast)
shopping_cart.add_product(milk)

assert toast in shopping_cart
assert milk in shopping_cart

shopping_cart2 = ShoppingCart()
shopping_cart2.add_product(toast)

assert toast in shopping_cart2

shopping_cart = shopping_cart | shopping_cart2  # combine two shopping charts


shopping_cart << baguette  # put a baguette into the shopping cart

assert baguette in shopping_cart
```