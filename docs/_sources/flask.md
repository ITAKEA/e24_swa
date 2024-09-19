# Flask API
I skal i dag lære at bruge det python web framework der hedder Flask. Og i skal kunne arbejde med en Sqlite database.
 
## Læringsmål
* Kunne oprette et rest API lavet med Flask
* Kunne arbejde med en SqlLite database
* Kunne inkludere api kald til eksterne api´er i en Flask applikation.

## Forberedelse
* [Create A Python API in 12 Minutes](https://www.youtube.com/watch?v=zsYIw6RXjfM) (12:03)
* [SQLite in Python || Python Tutorial || Learn Python Programming](https://www.youtube.com/watch?v=c8yHTlrs9EA)(10:10)

<!--
* [Python SQLite Tutorial: Build a Python project with a SQLite database](https://youtu.be/iXYeb2artTE?feature=shared&t=774)(23:00)
-->

Skim følgende dokumentation for Flask og SqLite

* [Flask Documentation](https://flask.palletsprojects.com/en/3.0.x/) 
    * obs: vi kommer ikke til at arbejde med html filer i dette semester.
* [sqlite3 — DB-API 2.0 interface for SQLite databases](https://docs.python.org/3/library/sqlite3.html)

Og evt denne:

* [SQLite Tutorial](https://www.w3resource.com/sqlite/)


## Dagens indhold

* Vi starter sammen med live coding af øvelsen herunder, og i bliver langsomt sat løs på egen hånd. 


## Materialer

* [Create A Python API in 12 Minutes](https://www.youtube.com/watch?v=zsYIw6RXjfM) (12:03)
* [SQLite in Python || Python Tutorial || Learn Python Programming](https://www.youtube.com/watch?v=c8yHTlrs9EA)(10:10)
* [Flask Documentation](https://flask.palletsprojects.com/en/3.0.x/) 
* [sqlite3 — DB-API 2.0 interface for SQLite databases](https://docs.python.org/3/library/sqlite3.html)
* [SQLite Tutorial](https://www.w3resource.com/sqlite/)
* [List Comprehension || Python Tutorial || Learn Python Programming](https://www.youtube.com/watch?v=AhSvKGTh28Q)(7:42)

## Øvelser
Kig på følgende diagram og opret et API der følger disse routes.

![](_static/img/Hvad_er_et_API.png)

1. I stedet for så lave det med `students` skal i lave det med `members`. 
2. I skal som udgangspunkt læse [denne liste med dictionaries](https://github.com/ITAKEA/kode_fra_undervisning_e24/blob/master/flask1/data_dict.py) som jeres datakilde.
1. Når i har fået det til at virke skal Api´et gemme og læse data i en Sqlite database. Det skal være det samme data som i listen, så i skal `INSERT` det i en tabel i databasen (`executemany`) 
2. Hver Member skal altså have følgende attributter:

``` 
    id, (primær nøgle og skal auto incrementeres) 
    first_name, 
    last_name, 
    birth_date, 
    gender, 
    email, 
    phonenumber, 
    address, 
    nationality,
    active,
    github_username
``` 

3. Man skal kunne se den enkelte members public github repositories som en del af json schemaet i feks. `api/members` routen (så det kan være at i skal ændre `github_username` på de 10 brugere til noget virkeligt). 
4. Hvis det member der vises er **DIG**, skal man også kunne se de private repositories.
5. I skal sørge for at de rigtige http statuskoder returneres med `http responset`.
6. Og Husk: der er regler for hvad der skal ske i et GIT POST, PUT, PATCH og DELETE request. De regler skal i følge. Her er det helt ok at spørge chatten om disse regler, men sørg for at skrive koden selv!
7. I skal også sørge for at fange eventuelle fejl, som et forkert id, forkert json i body osv.

