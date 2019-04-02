|Date|Version|Change Log|Author|
|:------:|:------:|:-----:|:-----:|
|25/03/2019|0.1|Create the document|Gabriel Ziegler|
|25/03/2019|0.2|Add PEP rules for classes and methods|Gabriel Ziegler|

## Python Style

The style guide used is Python's [PEP 8](https://www.python.org/dev/peps/pep-0008/)

* **snake_case**, NOT camelCase

Use:
```Python
class Person(models.Model):
    first_name = models.CharField(max_length=20)
    last_name = models.CharField(max_length=40)
```

Do **NOT** do the following:
```Python
class Person(models.Model):
    FirstName = models.CharField(max_length=20)
    Last_Name = models.CharField(max_length=40)
```

* 4 space indent

* 4 space indent for functions with big parameters

Use:
```Python
raise AttributeError(
    'Here is a multine error message '
    'shortened for clarity.'
)
```

Do **NOT** use:
```Python
raise AttributeError('Here is a multine error message '
                     'shortened for clarity.')
```

* Single quote for strings

* Function docstrings follow the [PEP 257](https://www.python.org/dev/peps/pep-0257/)

```Python
def test_foo():
    """
    A test docstring looks like this (#123456).
    """
    ...
```

* **Meta** class must be implemented just after class attributes and must be separated with just ONE line.

```Python
class Person(models.Model):
    first_name = models.CharField(max_length=20)
    last_name = models.CharField(max_length=40)

    class Meta:
        verbose_name_plural = 'people'
```

