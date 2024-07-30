# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Використовуючи BeautifulSoup, знайти всі заголовки статей на сайті [https://news.ycombinator.com/](https://news.ycombinator.com/) та надрукувати їх на консолі. 

## Підказка:

```py
# Потрібні наступні модулі: 

from bs4 import BeautifulSoup
import requests

url = 'https://news.ycombinator.com/'

# Отримати контент 
content = requests.get(url).content

# Створити екземпляр soup
soup = BeautifulSoup(content, 'html.parser')

```
