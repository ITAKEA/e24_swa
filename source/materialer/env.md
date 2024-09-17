# Miljøvariabler

Dette er en kort beskrivelse af hvordan man arbejder med miljøvariabler i VSCode og Python.    

## Opret en .env-fil

I roden af dit projekt, opret en fil med navnet `.env`. I denne fil, definer du dine miljøvariabeler på denne måde:

```
    GITHUB_ACCESS_TOKEN=din_adgangstoken_her
```

## Installer python-dotenv

Installer modulet  `python-dotenv`:

```
    pip install python-dotenv
```

## Indlæs .env-filen i dit Python-script

Brug `dotenv`-modulet til at indlæse værdierne fra din `.env`-fil.

```python
from dotenv import load_dotenv
import os
import requests

# Indlæs miljøvariabler fra .env-fil
load_dotenv()

# Hent token
github_token = os.getenv('GITHUB_ACCESS_TOKEN')

# Brug token i en forespørgsel
headers = {
    "Authorization": f"token {github_token}"
}

url = "https://api.github.com/repos/clbokea/linux"
response = requests.get(url, headers=headers)

print(response.json())
```
## Skriv .env i din .gitignore
For at undgå at du pusher dine miljøvariabler til Github skal du tilføje `.env` til din `.gitignore` fil.

 
