# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Створити клас Circle. 
Конструктор класу приймає 3 параметри:
- x, y - координати центру кола
- r - радіус кола

Клас повинен мати такі методи:

```py

    def length(self):
        """Повертає довжину кола."""
    

    def square(self):
        """Повертає площу кола."""
    

    def set_r(self, r):
        """Встановлює радіус кола."""

```

Вхідні дані та результат:

```py
c = Circle(3, 4, 1)
print(c.length(), c.square())  
# 6.283185307179586 3.141592653589793
c.set_r(-1)  
# AssertionError: Радіус має бути позитивним числом!
```

Підказка:
- Використовуйте модуль math для розрахунку довжини та площі кола за формулами:
```py
math.pi * r
math.pi * r**2
```
