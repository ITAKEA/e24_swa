# Azure Cheatsheet
Følgende kan i bruge som en slags noter eller reminders til hvad vi har været igennem i deploy sessionerne.

## Deployment -> Deployment Center
* Her opsætter vi forbindelsen til **Github (Github Actions)** og forbindelse **DockerHub**

## Settings -> Environment Variables
* Her tilføjes Environment variablerne. 
* Det er også her at variablen **WEBSITES_ENABLE_APP_SERVICE_STORAGE** skal sættes til **true** hvis vi vil bevare vores database henover gentagne deployments.

I undervisning så mine (claus) environment variabler til api-gateway sådan ud:

![](../_static/img/env.png)

og til github_microservice sådan:

![](../_static/img/env2.png)

## WEBSITES_ENABLE_APP_SERVICE_STORAGE
Hvis denne variabel sættes til **true** vil alle filer der ligger i Azure Web Appens `/home` mappe forblive liggende når vi deployer et nyt image.    
Dette kan vi udnytte til at vi ligger vores database fil i denne mappe.    
Det gøre ved at lave en miljøvariabel i vores kode feks. `DB_PATH = os.getenv('SQLITE_DB_PATH')` og så lave en ny environment variabel `SQLITE_DB_PATH : /home/users.db` (som beskrevet oven over).    

