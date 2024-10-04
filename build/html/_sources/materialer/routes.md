# Routes og queri parametre

Vi har indtil nu arbejdet med routes der bruger følgende logik:

```
GET students/
GET students/1
...
```

En anden mulighed er at bruge det der hedder queries parametre.

```
GET students?id=1
GET students?name=Claus&age=23
...
```

Når du i koden skal håndtere dette vil du gøre det på følgende måde.

```
@app.route('/students', methods=['GET'])
def get_student():
    name = request.args.get('name')
    age = request.args.get('age')

...

```
