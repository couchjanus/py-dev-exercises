# py-dev-exercises
Python practice exercises

- This is the *[Exercises for py-dev project](https://github.com/couchjanus/py-dev-exercises)*.

1. Створити пакет, що містить модулі системи моніторингу цілісності файлової системи заданих каталогів.

### Пакет міститься в директорії fims з такою структурою:

```
├── helpers.py
├── __init__.py
├── __main__.py
├── monit.py
├── __pycache__
└── shelve.db.db

```

### Модуль helpers.py повинен містити функції:

```py

def hello(TITLE):
    print(F"Hi! It’s me, {TITLE.upper()}")

def bye(TITLE):
	print(f'Thanks for using {TITLE}')

```

### Модуль '__init__.py' повинен містити визначення назви та версії програми, а також константу TITLE, наприклад:

```py

__app_name__ = "fims"
__version__ = "0.1.0"
TITLE = "File Integrity Monitoring System"

```
### Модуль '__init__.py' також повинен містити визначення списку каталогів, що будуть моніторитись, наприклад:

```py

monitor = [
   {
     'path':'/home/janus/projects/py.dev/monitoring',
     'recursive':True
   },
   {
      'path':'/home/janus/projects/py.dev/monitoring/no-recursive', 
      'recursive':False
   }
]

```
### В модулі '__init__' потрібно визначити місце-знаходження постійного сховища хешу кожного файлу, що підлягає моніторингу, наприклад:

```py

DATABASE_PATH = os.path.dirname(os.path.realpath(__file__))

DATABASE_NAME = "shelve.db"

DATABASE = f"{DATABASE_PATH}/{DATABASE_NAME}"
```

### Модуль monit.py містить функцію:

```py

def getFiles(monitor):
	filesList=[]

	for x in monitor:
		if os.path.isdir(x['path']):
			if x['recursive']:
				filesList.extend([os.path.join(root, f) for (root, dirs, files) in os.walk(x['path']) for f in files])
			else:
				filesList.extend([item for item in os.listdir(x['path']) if os.path.isfile(item)])
		elif os.path.isfile(x['path']):
			filesList.append(x['path'])
	return filesList

```

### Модуль __main__.py містить наступний код:

```py

def main():
   helpers.hello(TITLE)

   files={}
    
   while True:
      for file in monit.getFiles(monitor):
         hash = hashlib.sha256()

         with open(file) as f:
            for chunk in iter(lambda: f.read(2048), ""):
               hash.update(chunk.encode("utf-8"))
               sha256 = hash.hexdigest()

               if file in files and sha256 != files[file]:
                  print(f'{file} has been changed! {time.strftime("%Y-%m-%d %H:%M:%S")}')
                  
               files[file]=sha256
               with shelve.open(DATABASE) as s:
                  s[file] = files[file]

            time.sleep(1)

if __name__ == "__main__":
   try:
      main()
   except KeyboardInterrupt:
      helpers.bye(TITLE)

```

### Запуск пакету на виконання:

```bash
python -m fims
```
