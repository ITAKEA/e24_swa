
# Ex 1. Get, Post, Put, Patch og Delete**

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


