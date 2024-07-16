# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Маємо клас Rectangle:

```py
# test_get_area_rectangle.py: Our code to be tested
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
 
    def get_area(self):
        return self.width * self.height
 
    def set_width(self, width):
        self.width = width
 
    def set_height(self, height):
        self.height = height
```

Потрібно написати клас TestGetAreaRectangle, що містить 2 тестові функції test_normal_case та test_negative_case.
- Тестова функція test_normal_case перевіряє, що площа прямокутника з шириною width=2 та висотою height=3 дорівнює 6.
- Тестова функція test_negative_case перевіряє, що площа прямокутника з шириною width=-1 та висотою height=2 генерує AssertionError: неправильний негативний результат.

- Класи Rectangle та TestGetAreaRectangle містяться у файлі test_get_area_rectangle.py.
- Запустити модульний тест PyTest за допомогою:

```bash
python -m pytest test_get_area_rectangle.py
```

## Результат тестування виглядає наступним чином
```bash

collected 2 items                                                                       

test_get_area_rectangle.py .F                                                                         [100%]

======================================== FAILURES ========================================
________________________ TestGetAreaRectangle.test_negative_case _________________________

self = <test_get_area_rectangle.TestGetAreaRectangle object at 0x749baeb225d0>

    def test_negative_case(self):
        """expect -1 as output to denote error when looking at negative area"""
        rectangle = Rectangle(-1, 2)
>       assert rectangle.get_area() == -1, "incorrect negative output"
E       AssertionError: incorrect negative output
E       assert -2 == -1
E        +  where -2 = <bound method Rectangle.get_area of <test_get_area_rectangle.Rectangle object at 0x749bae356e10>>()
E        +    where <bound method Rectangle.get_area of <test_get_area_rectangle.Rectangle object at 0x749bae356e10>> = <test_get_area_rectangle.Rectangle object at 0x749bae356e10>.get_area

test_get_area_rectangle.py:24: AssertionError
================================ short test summary info =================================
FAILED test_get_area_rectangle.py::TestGetAreaRectangle::test_negative_case - AssertionError: incorrect negative output
============================== 1 failed, 1 passed in 0.14s ===============================
```

## Підказка:

Використовуйте вбудоване в Python ключове слово assert при написанні функцій test_normal_case та test_negative_case. Наприклад

```py
assert rectangle.get_area() == 6, "incorrect area"
```