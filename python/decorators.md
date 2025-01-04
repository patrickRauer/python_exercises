# Decorators

## Timing decorator
For the beginning we will start with a *timing decorator*, which
should print the needed time of the applied function.  
Let's assume we have this function:
```python
def some_function(number: int = 100) -> int:
    """
    Some function to use
    
    :param number: The number of iterations
    :returns: The sum of all iterations
    """
    total_number: int = 0
    for i in range(number):
        total_number += i
    return total_number
```

### Exercises
* Write a decorator which stores the current time before the start and after the function is finished.
* Make sure, that (meta) information of the function are right (see test case)
* Sometimes it is not possible to use the @ annotation. How can a decorator be used without the @?

```python
@timing_decorator
def some_function(number: int = 100) -> int:
    """
    Some function to use
    
    :param number: The number of iterations
    :returns: The sum of all iterations
    """
    total_number: int = 0
    for i in range(number):
        total_number += i
    return total_number


assert some_function.__name__ == 'some_function' 
assert some_function.__annotations__ == {'number': int, 'return': int}
```