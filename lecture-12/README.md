# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Маємо клас Contact:

```py
class Contact:
    def __init__(self, name, phone, address):
        self.name = name
        self.phone = phone
        self.address = address

    def to_json(self):
        '''Serialize the object custom object'''

        return json.dumps(self, default=lambda o: o.__dict__, sort_keys=True, indent=4)        

```

Маємо екземпляри c1,c2 класу Contact:

```py
c1 = Contact("Lucy Smile", '7777', '1, Smile st.') 
c2 = Contact("Thomas Cook", '1123', '2, Cook avn.')
```
Потрібно створити список контактів contacts, додавши до нього екземпляри c1,c2

Створений список потрібно серіалізувати та записати у файл filename = "contact.json" 
Результат серіалізації:

```json
["{\n    \"address\": \"1, Smile st.\",\n    \"name\": \"Lucy Smile\",\n    \"phone\": \"7777\"\n}", "{\n    \"address\": \"2, Cook avn.\",\n    \"name\": \"Thomas Cook\",\n    \"phone\": \"1123\"\n}"]
```

Після створення файлу contact.json, потрібно виконати десеріалізацію файлу, створивши список result.
Результат десеріалізації:

```py

[{'address': '1, Smile st.', 'name': 'Lucy Smile', 'phone': '7777'}, {'address': '2, Cook avn.', 'name': 'Thomas Cook', 'phone': '1123'}]

```

Підказка:
- Використовуйте метод json.dump для серіалізації у файл
- Використовуйте метод json.load для десеріалізації з файлу
- Використовуйте метод json.loads для десеріалізації рядка
