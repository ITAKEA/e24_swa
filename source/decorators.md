# Python  - Decorators
I har i jeres Flask applikationer set det lille '@' brugt over forskellige funktioner. I dag skal i lære hvad det er og hvordan i bruger det i jeres python programmer.

I Flask applikationer ser i dette: 

```
@app.route('/')
```

Det hedder en **decorator** og det er et super vigtigt element i en pythonic måde at lave softwarearkitektur på. Decorators tilhører det paradigme der hedder funktionelprogrammering. 

Det funktionelle programmeringsparadigme fokuserer på at skrive kode ved hjælp af rene funktioner. Rene funktioner returnerer altid samme output for samme input og har ingen bivirkninger. Med bivirkninger menes det, at funktioner ikke ændrer programmets tilstand, såsom at ændre værdien af en global variabel, skrive data til en fil eller bruge print-statements inden i funktioner. Alt andet end en returværdi betragtes som en bivirkning. Paradigmet gør også brug af højere-ordens funktioner, som kan tage andre funktioner som argumenter eller returnere dem, hvilket er centralt for dekoratorer. Samlet set gør dette paradigme koden lettere at forstå, teste og vedligeholde.

Det er den pythonic måde at udbygge funktionalitet til eksisterende funktioner. En måde at følge DRY principperne, og en måde at følge Open/Closed princippet fra SOLID.    

Det er desværre også et super svært emne at forstå, men vi kaster os ud i det, og med en skridt for skridt tilgang er det som alt andet i livet muligt at mestre. 

## Læringsmål

* Kunne forstå og bruge Open/Closed designprincippet i forhold til funktioner.


## Forberedelse
I skal læse og gennemgå de følgende 5 artikler/tutorials

* [Xmas decoration, part 1](https://www.bitecode.dev/p/xmas-decoration-part-1)
* [Xmas decoration, part 2](https://www.bitecode.dev/p/xmas-decoration-part-2)
* [Xmas decoration, part 3](https://www.bitecode.dev/p/xmas-decoration-part-2)

For at kunne forstå decorators er det en forudsætning at i har **godt** styr på funktioner. 

* definition
* parametre
* return værdi og type
* reference til funktioner
* kald af funktioner

Så det er evt. en god ide at kigge denne artikkel igennem [Holding references on classes and functions](https://www.bitecode.dev/p/holding-references-on-classes-and)

## Dagens indhold





## Materiale

* [Xmas decoration, part 1](https://www.bitecode.dev/p/xmas-decoration-part-1)
* [Xmas decoration, part 2](https://www.bitecode.dev/p/xmas-decoration-part-2)
* [Xmas decoration, part 3](https://www.bitecode.dev/p/xmas-decoration-part-2)

* [primer-on-python-decorators](https://realpython.com/primer-on-python-decorators/)

### Øvelser

#### Øv 4: Analyser denne kode
Kig på følgende kodeeksempel og forklar hvad der foregår.    
Du skal først kunne forklare det helt overordnet, altså hvad er resultatet af at køre denne kode.    
Dernest skal du skrive en skridt for skridt forklaring af flowet i koden. Numerer alle væsentlige linier i kode med en beskrivelse af hvad der sker.


```
from flask import Flask, jsonify, request
import sqlite3
import os

app = Flask(__name__)
DATABASE = 'tutorial.db'

def ensure_db_exists(db_path):
    def decorator(func):
        def wrapper(*args, **kwargs):
            if not os.path.exists(db_path):
                # Create database file and 'movies' table
                with sqlite3.connect(db_path) as conn:
                    conn.execute('''
                        CREATE TABLE movies(
                            title TEXT,
                            year INTEGER,
                            score REAL
                        )
                    ''')
            else:
                # Ensure the 'movies' table exists in the existing database
                with sqlite3.connect(db_path) as conn:
                    conn.execute('''
                        CREATE TABLE IF NOT EXISTS movies(
                            title TEXT,
                            year INTEGER,
                            score REAL
                        )
                    ''')
            return func(*args, **kwargs)
        return wrapper
    return decorator

def connect_db(db_path):
    def decorator(func):
        def wrapper(*args, **kwargs):
            with sqlite3.connect(db_path) as conn:
                with conn:  # Ensures that the commit is called automatically
                    cur = conn.cursor()
                    return func(cur, *args, **kwargs)
        return wrapper
    return decorator

def execute_query(query, params=()):
    def decorator(func):
        def wrapper(cur, *args, **kwargs):
            cur.execute(query, params)
            if query.lstrip().upper().startswith("SELECT"):
                res = cur.fetchall()
                movies = [dict(zip([column[0] for column in cur.description], row)) for row in res]
                return func(movies, *args, **kwargs)
            else:
                return func(None, *args, **kwargs)
        return wrapper
    return decorator

@app.route('/movies', methods=['GET', 'POST'])
@ensure_db_exists(DATABASE)
@connect_db(DATABASE)
def movies(cur):
    if request.method == 'GET':
        @execute_query('SELECT * FROM movies')
        def get_movies(movies, *args, **kwargs):
            return jsonify(movies)
        return get_movies(cur)

    elif request.method == 'POST':
        data = request.json
        title = data.get('title')
        year = data.get('year')
        score = data.get('score')

        @execute_query('INSERT INTO movies (title, year, score) VALUES (?, ?, ?)', (title, year, score))
        def insert_movie(movies, *args, **kwargs):
            return jsonify({'message': 'Movie added successfully!'}), 201

        return insert_movie(cur)

if __name__ == '__main__':
    app.run(debug=True)
```

#### Øv 3: Tutorial
Se følgende video og skriv selv hans eksempler (i en jupyter notebook)
* [What Does It Take To Be An Expert At Python? (decorators)](https://youtu.be/cKPlPJyQrt4?si=RgFuHWHpIqzUlMtE&t=2841) (Fra 47:20 til 1:06:31)
