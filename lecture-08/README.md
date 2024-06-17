# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Функція Фібоначчі викликає саму себе кілька разів з тим самим вводом. 

```py

def fibonacci_of(n):
   if n in {0, 1}:  # Base case
       return 1
   return fibonacci_of(n - 1) + fibonacci_of(n - 2)  # Recursive case

print([fibonacci_of(n) for n in range(15)])
# [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610]

```
Замінити рекурсивний метод генерації послідовності Фібоначчі, написавши функцію fib(), що повертає згенероване значення послідовності Фібоначчі, використовуючи оператор yield

```py
def fib():
    a, b = 0, 1
    while True:
        yield b
        ...

fib_list = []

for n in fib():
    if n > 610: break
    fib_list.append(n)

print(fib_list)
# [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610]

```
Підказка:
- Коли функція fib() викликається вперше, вона встановлює a в 0 і b в 1, а потім повертає b. 
- Коли fib відновлюється, з її точки зору оператор yield насправді такий самий, як оператор print: Виконання fib продовжується після yield з усіма локальними станами. a і b отримують значення  1 і 1, і функція fib повертається до yield, надаючи 1 ініціатору. І так далі. 
