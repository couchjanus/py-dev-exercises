# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Додайте до схем departments.py і roles.py методи редагування та видалення записів. Декоруйте методи наступними маршрутами:

```py

# departments.py 

@bp.route("/departments/create", methods=('GET', 'POST'))
@login_required
def create():
    #

@bp.route('/departments/<int:id>/update', methods=('GET', 'POST'))
@login_required
def update(id):
    #

@bp.route('/departments/<int:id>/delete', methods=('POST',))
@login_required
def delete(id):
    #

# roles.py 

@bp.route("/roles/create", methods=('GET', 'POST'))
@login_required
def create():
    #

@bp.route('/roles/<int:id>/update', methods=('GET', 'POST'))
@login_required
def update(id):
    #

@bp.route('/roles/<int:id>/delete', methods=('POST',))
@login_required
def delete(id):
    #

```
2. Додати до шаблонів сторінок для відображення списків департаментів та ролей стовпчик, що містить кнопки з посиланнями на методи редагування та видалення відповідних записів.
3. Створити шаблони сторінок, що містять форми редагування певного департаменту та ролі.
