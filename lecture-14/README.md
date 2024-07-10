# py-dev-exercises
Python practice exercises 

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Маємо модуль cli:

```py
from todo.model import Todo
from todo.todos import TodoList

from rich.console import Console
from rich.table import Table
from pathlib import Path
from todo import __app_name__, __version__, TITLE, ERRORS

from todo.helpers import add_your_task, hello, make_your_choice, bye, help_me, choose_category
import typer
from todo import db, config, todos
from typing import Any, Annotated

app = typer.Typer()

console = Console()

header = Todo.make_header()

def show(tasks: Any) -> None:
    
    table = Table(show_header=True, header_style="bold blue")

    for item in header:
        table.add_column(item['name'], style=item['style'], width=item['width'], min_width=item['min_width'], justify=item['justify'])

    for index, task in enumerate(tasks, start=1):
        c = Todo.get_category_color(task['category'])
        is_done = Todo.DONE if task['status'] == 2 else Todo.PENDING
        table.add_row(str(index), task['task'], f'[{c}]{task['category']}[/{c}]', is_done)

    console.print(table)

def get_todo_list() -> todos.TodoList:
    if config.CONFIG_FILE_PATH.exists():
        db_path = db.get_database_path(config.CONFIG_FILE_PATH)
    else:
        typer.secho('Config file not found. Please, run "todo init"', fg=typer.colors.RED, )
        raise typer.Exit(1)
    if db_path.exists():
        return todos.TodoList(db_path)
    else:
        typer.secho('Database not found. Please, run "todo init"', fg=typer.colors.RED, )
        raise typer.Exit(1)

@app.command()
def init(
    db_path: Annotated[str, typer.Option("--db-path", "-db", prompt="to-do database location?"),]=str(db.DEFAULT_DB_FILE_PATH),) -> None:

    app_init_error = config.init_app(db_path)

    if app_init_error:
        typer.secho(f"Creating config file failed with {ERRORS[app_init_error]}", fg=typer.colors.RED)
        raise typer.Exit(1)
    
    db_init_error = db.init_database(Path(db_path))
    if db_init_error:
        typer.secho(f"Creating database failed with {ERRORS[app_init_error]}", fg=typer.colors.RED)
        raise typer.Exit(1)
    
    typer.secho(f"The todo database is {db_path}", fg=typer.colors.GREEN)


@app.command()
def run() -> None:
    hello()
    todo_list = get_todo_list()

    while True:
        match make_your_choice():
            case 'a':
                category = choose_category()
                task = add_your_task()
                
                current_todo, write_error = todo_list.add(task, category)

                if write_error:
                     typer.secho(f"Added task failed with {write_error}", fg=typer.colors.RED)
                     raise typer.Exit(1)
                
                typer.secho(f"Task {task} was added to todo database with {category}", fg=typer.colors.GREEN)


            case 'l':
                tasks, error = todo_list.get_todo()
                if error:
                    typer.secho(f"Fetching tasks failed with {ERRORS[error]}", fg=typer.colors.RED)
                    raise typer.Exit(1)
                else:
                    if len(tasks) == 0:
                        typer.secho("There are no tasks in the to-do list yet", fg=typer.colors.RED)
                        raise typer.Exit()
                    show(tasks)
            case 'u':
                id = helpers.choose_id()
                tasks, error = todo_list.complete(id)
                show(tasks)
            case 'r':
                id = helpers.choose_id()
                tasks, error = todo_list.delete(id)
                show(tasks)
            case 'q':
                bye(TITLE)
                break

            case _:
                help_me()
```

Підключити систему журналювання, що записує до файлу todo.log повідомлення про успіх чи помилку виконання операцій додавання, перегляду, оновлення та видалення завдання при роботі з базою даних.

2. Встановити модуль pylint. Виконайте перевірку пакету todo:

```sh
pylint todo
```

Виправте критичні помилки, що будуть знайдені pylint у модулях пакету todo.