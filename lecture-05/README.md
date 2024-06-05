# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Є файл sales.txt, який містить щомісячні дані про продажі товарів. Знайти у файлі рядок про продаж товару laptop, надрукувати цей рядок та його номер. 

файл sales.txt: 
```
mouse 100
mobile 20
USB 39
USB 39
USB 39
laptop 30
board 12
```

Підказка: 
- Відкрити файл у режимі читання. 
- Використовуйте метод readlines(), щоб отримати всі рядки з файлу у формі об’єкта списку.
- Використовуйте цикл для кожного рядка з файлу.
- В кожній ітерації циклу використовуйте умову if, щоб перевірити, чи присутній рядок у поточному рядку, і, якщо присутній, виведіть поточний рядок разом із номером рядка.

2. У вас є файл із такими реченнями: Peter Piper picked a peck of pickled peppers. A peck of pickled peppers Peter Piper picked. Where's the peck of pickled peppers Peter Piper picked.
Потрібно вставити нове речення (If Peter Piper picked a peck of pickled peppers) після другого речення в той самий рядок. 

Бажаний результат: Peter Piper picked a peck of pickled peppers. A peck of pickled peppers Peter Piper picked. If Peter Piper picked a peck of pickled peppers. Where's the peck of pickled peppers Peter Piper picked.

Підказка:
- Прочитати речення з файлу,
- Внести необхідні зміни,
- Записати його в новий файл. 
- Використовуйте метод splitlines(), який повертає список рядків, розбитих на межі рядків.

3. Модуль pathlib має функції: 
- read_text(), що читає текстовий файл 
- path.read_text().count("\n") читає текстовий файл і обчислює кількість рядків шляхом підрахунку рядків.
- len(path.read_text().split()) читає текстовий файл і обчислює кількість слів
- len(path.read_text()) читає текстовий файл і обчислює кількість символів, знаходячи довжину рядка.

Написати скрипт, що може читати один або декілька текстових файлів і повідомляти, скільки рядків, слів і символів містить кожен із файлів. 

4. Написати скрипт виводу квадрата заданого числа
Використовуючи модуль argparse, додати до скрипта підказку при виклику програми: python prog.py --help

потрібно отримати такий результат:
```
usage: square.py [-h] [-v] square

positional arguments:
  square         display a square of a given number

options:
  -h, --help     show this help message and exit
  -v, --verbose  increase output verbosity

```
