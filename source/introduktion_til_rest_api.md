# En introduktion til REST API


## Læringsmål

Når denne dag er slut, bør du kunne svare på disse spørgsmål:

- Hvad er fordelene ved at bruge et RESTful API?
- Hvad er ideen bag de følgende arkitektoniske begrænsninger, der anvendes af REST
    - Uniform Interface
    - Stateless
    - Cacheable
    - Client-Server
    - Layered System
- Hvad er JSON, hvilken struktur har den, og hvorfor passer JSON så godt sammen med REST
- Hvordan bruger man Postman til at teste en RESTful API?
- Hvordan bruger man dokumentationen til et API
- Hvordan og hvorfor skal jeg bruge API keys til authendication
- Hvorfor er Http statuskoder vigtige i forhold til REST API 

## Forberedelse

* Åben Chat-GPT og Copy / Paste spørgsmålene fra læringsmålene ovenover ind og læs svarene den kommer med (30 min)
* Hvis du ikke allerede har **[Postman](https://www.postman.com/downloads/)** på din computer, skal du installere det før vi mødes i klassen (Der er ikke behov for at oprette en konto) (5 min)
* [Introduction to REST (22 min)](https://www.youtube.com/watch?v=fqX4BpIWu4s)
* [Architectural Constraints used by Rest (17 min)](https://www.youtube.com/watch?v=u7HWkKhIYbU)
    * (5:50) Manden (Lars) snakker om localhost:8080/api/players. Dette projekt kommer vi ikke til at arbejde med dette semester, men i stedet med microservices.

## Dagens indhold

Vi starter med en gennemgang af [Øv 1: Download filer](https://github.com/ITAKEA/kode_fra_undervisning_e24/tree/master/python3/exercises/solutions) øvelsen.
Og [Pandas øvelsen]()

Herefter gennemgår vi kort i overskrifter af hvad i forventes at have lært derhjemme. 

Dette inkluddere disse sider: 

* [Http protokollen](materialer/http.md) 

---
![](../_static/img/JSON.png)
---
![](../_static/img/Hvad_er_et_API.png)
--- 
![](../_static/img/http_status.png)
---

Resten af dagen bliver med Ping/pong øvelser/gennemgang ved tavlen.
 
* Vi starter med: Tutorial: [Github API](materialer/tutorial_github_api.md)
* Se (og skriv) disse tutorial: [Interacting With REST APIs and Python](https://realpython.com/courses/interacting-rest-apis-python/)
    * I skal kun se den gratis del af videoerne (1-5)


## Materialer
* []()

### Øvelser

**Ex 1. Get, Post, Put, Patch og Delete**

I denne øvelse skal i gøre brug af dette api [https://jsonplaceholder.typicode.com/](https://jsonplaceholder.typicode.com/) og du skal bruge Postman til at lave dine forespørgelser.

Du kan se nederst på siden hvilke resourcer der er tilrådeighed i dette API.

1. **GET:**
    - Hent alle brugere: **`GET /users`**
    - Hent et bestemt indlæg: **`GET /posts/{id}`** (erstat **`{id}`** med det ønskede indlægs ID)
    - Hent kommentarer til et bestemt indlæg: **`GET /posts/{id}/comments`** (erstat **`{id}`** med det ønskede indlægs ID)
2. **POST:**
    - Opret en ny bruger: **`POST /users`**
    - Opret et nyt indlæg: **`POST /posts`**
    - Opret en ny kommentar til et indlæg: **`POST /comments`**
3. **PUT:**
    - Opdater en brugers oplysninger: **`PUT /users/{id}`** (erstat **`{id}`** med den ønskede brugers ID)
    - Opdater et indlæg: **`PUT /posts/{id}`** (erstat **`{id}`** med det ønskede indlægs ID)
4. **PATCH:**
    - Opdater en brugers delvise oplysninger: **`PATCH /users/{id}`** (erstat **`{id}`** med den ønskede brugers ID)
    - Opdater delvist et indlæg: **`PATCH /posts/{id}`** (erstat **`{id}`** med det ønskede indlægs ID)
5. **DELETE:**
    - Slet en bruger: **`DELETE /users/{id}`** (erstat **`{id}`** med den ønskede brugers ID)
    - Slet et indlæg: **`DELETE /posts/{id}`** (erstat **`{id}`** med det ønskede indlægs ID)
    - Slet en kommentar: **`DELETE /comments/{id}`** (erstat **`{id}`** med den ønskede kommentars ID)


