# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Є код простої програми-калькулятора на Python. Він містить функції додавання, віднімання, множення, ділення, цілочисельного ділення та операцій за модулем, а також меню та довідкову систему. 

# файл calc.py: 
```py
title = "Super Calc"

# Program makes a simple calculator that can add, subtract, multiply and divide using functions

# define functions
def add(x, y):
    """This function adds two numbers"""
    return x + y

def subtract(x, y):
    """This function subtracts two numbers"""
    return x - y

def multiply(x, y):
    """This function multiplies two numbers"""
    return x * y

def divide(x, y):
    """This function divides two numbers"""
    return x / y

def modulo(x, y):
    """This function finds the modulus of two numbers"""
    return x % y

def idivide(x, y):
    """This function integer divides two numbers"""
    return x // y

def exponent(x, y):
    """This function raises x to the power of y"""
    return x ** y

ops = {
    '+': add,
    '-': subtract,
    '*': multiply,
    '/': divide,
    '//': idivide,
    '%': modulo,
    '**': exponent
}

def menu():
    print(f"{title}".title().center(40, '='), '\n')
    print("_"*40)
    str1 = 'Select operation:'
    print('|' + str1 + ' ' * (38 - len(str1)) + '|')
    print('|' + "_"*38 + '|')
    print("| c : Calculate".ljust(39, ' ') + '|')
    print("| h : Help".ljust(39, ' ') + '|')
    print("| q : Quit".ljust(39, ' ') + '|')
    print("="*40)

    choice = input("| Enter choice (h|c|q): ".title()).lower()
    return choice if choice in ('h', 'c', 'q') else 'h'

def extract(entry):
    for o in ops.keys():
        if o in entry:
            parts = entry.split(o)
            if len(parts) == 2:
                a, b = parts
                return a.strip(), b.strip(), o
    return None, None, None

def calc_help(e=''):
    if e:
        print(f"\n{e}")
    print("""
        Usage operation:
            h                        Display this usage message
            2 + 2                    Add
            3 - 1                    Subtract
            2 * 2                    Multiply
            4 / 2                    Divide
            5 // 2                   Int Divide
            7 % 3                    Modulo Divide
            2 ** 3                   Exponentiation
            q                        Quit
        """)

def result(a, b, operator):
    """This function returns the result"""
    try:
        a, b = float(a), float(b)
        if operator == '/' and b == 0:
            return None, "Oops, division by zero"
        elif operator in ('//', '%') and b == 0:
            return None, "Oops, division or modulo by zero"
        else:
            return ops[operator](a, b), ''
    except ValueError:
        return None, "Invalid input. Please enter numeric values."

while True:
    choice = menu()

    if choice == 'q':
        print('Thank you for using Super Calc!')
        break
    
    if choice == 'h':
        calc_help()
        continue

    if choice == 'c':
        entry = input("Enter x operator y (e.g., 2 + 2): ")
        a, b, operator = extract(entry)
        
        if not operator:
            calc_help("Invalid format or unsupported operator.")
            continue
        
        res, err = result(a, b, operator)
        if err:
            print(err)
        else:
            print(f"{a} {operator} {b} = {res}")

```

Переписати програму калькулятора, використовуючи методику створення пакету модулів.
