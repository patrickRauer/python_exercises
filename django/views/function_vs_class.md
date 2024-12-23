# Function based views and class based views

## Function based views
```python
from django.shotcuts import render
from django.http import HttpRequest, HttpResponse


def index(request: HttpRequest) -> HttpResponse:
    return render(
        request,
        'main/index.html',
        context={
            'title': 'Index page'
        }
    )
```

### Exercises

* Give the whole path of the used template relative the project root
* Describe the differences for a login user and for a random user
* **HttpResponse** has a property **status**. What is the value in this case?


## Class based views
```python
from django.views.generic import TemplateView


class IndexView(TemplateView):
    template_name: str = 'main/index.html'

    def get_context_data(self, **kwargs: dict) -> dict:
        return {
            'title': 'Index page'
        }
```

### Exercises

* Where is the input request object (aka. **HttpRequest**)?
* Which HTTP methods are allowed?
* Are there any differences to the *function* based view variant in the sense how it behaves?

## More class based views
```python

```