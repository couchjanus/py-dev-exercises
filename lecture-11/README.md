# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. За хвилину до обіду Вінні-Пух запитує кожні 5 секунд: "Вже майже час обіду?", викликаючи функцію it_may_be(name = ''):

```py
@delay(5)
def it_may_be(name = ''):
   return (name + " ask: It's nearly Luncheon Time? \n")
```
Напишіть функцію-декоратор delay(seconds), що викликає декоровану функцію it_may_be(name = '') з затримкою в 5 секунд.

### Вхідні дані: 

```py
# Вінні-Пух запитує: "Вже майже час обіду?"
for t in range(12):
    print(it_may_be(name = 'Winnie-the-Pooh'))
```

### Вихідні дані:

```py
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
# Winnie-the-Pooh ask: It's nearly Luncheon Time? 
```

### Підказка:
- Використовуйте модуль time, що містить функцію sleep, яка призупиняє виконання коду на певну кількість секунд.
