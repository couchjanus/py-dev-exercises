# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Створити схеми departments.py і roles.py та підключити їх до проекту. Схеми повинні включати методи побудови списку департаментів та ролей, а також метод створення нового департаменту та нової ролі. Декоруйте методи наступними маршрутами:

```py

# departments.py 
@bp.route("/departments/index")
def index():
    #

@bp.route("/departments/create")
def create():
    #

# roles.py 
@bp.route("/roles/index")
def index():
    #

@bp.route("/roles/create")
def create():
    #
```
2. Використовуючи Bootstrap, створити шаблони сторінок для відображення списків департаментів та ролей у вигляді таблиць.
3. Використовуючи Bootstrap, створити шаблони сторінок, що містять форми створення нового департаменту та нової ролі.
