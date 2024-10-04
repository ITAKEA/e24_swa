SoftwareArkitektur & Cloud, ITA 3. semester
===========================================

Materialet på denne side er kompendiet til faget Softwarearkitektur og faget Cloud på ITA uddannelsens 3. semester på KEA.  

Læringsmålene (SoftwareArkitektur)  
----------------------------------
Software arkitektur refererer til det overordnede strukturelle design af et software system (applikation), som definerer dets hovedkomponenter og deres interaktion med hinanden. 

En veldefineret og velstruktureret softwarearkitektur er vigtigt, da det sikrer systemets pålidelighed, skalerbarhed og vedligeholdelse og en god arkitektur fremmer derved muligheden for fejlretning og fremtidige udvidelser.    

Desuden fremmer det samarbejde mellem udviklingsteams ved at give en klar forståelse af systemets opbygning.

Vi kommer i dette fag til at arbejde med emner som at udvikle software ud fra forskellige programmeringsparadigmer som 

* Procedural programering 
* OOP 
* Funktionel programering 
  
I skal kunne bruge disse forskellige paradigmer, kunne foklare logikken i dem og kunne vurdere hvornår  i bruger den ene fremfor den anden.

Vi kommer til at arbejde udfra en række af softwaredesignprincipper som 

* SOLID 
* KISS 
* DRY 
* GRASP  

Disse principper skal i kunne bruge i forbindelse med udvikling af kode udfra de ovenstående paradigmer, og i skal kunne forklare hvorfor i har valgt at bruge netop det ene fremfor det andet.

Hvis andre skal kunne bruge vores applikationer er vi nød til at foklare dem hvordan. Derfor er dokumentation af kode, api og brug gennerelt alt afgørende for en applikations success.
Vi kommer derfor  desuden til at bruge en del tid på dokumentering af kode og api´er gennem:

* Readme filer til repositories på github
* Swagger til dokumentation af jeres API endpoints
* MkDocs til generel dokumentation af jeres kode og projekter.

Hvis kode skal være pålidelig, altså at vi kan være sikre på at det ikke fejler når vi sætter det i produktion, bliver vi nød til at teste det. Som teknik til dette kommer vi til at arbejde med Software testing gennem

* Doctests

Det overordnede arkitektoniske rammeværktøj på dette semester bliver **Microservices**.     
Microservices er som ordet hendtyder små programmer (services) der hver især tager sig af en lille del af den samlede helhed et system skal udføre.     
Hver service tager imod input og leverer et output gennem et restfull API, og hver service er deployet i en Docker Container. 

For at dette kommer til at fungerer skal i lære at bruge et Web Framework der hedder 

* Flask 
  
og som i vores tilfælde leverer API endpoints.

De samlede læringsmål for hele semesteret i Softwarearkitektur er:
------------------------------------------------------------------

* Have viden om, kunne bruge og forklare brugen af forskellige programeringsparadigmer som Procedural, OOP, funktionel, declarativ –programering. 
* Have teoretisk viden om Microservicearkitektur.  
* Kunne udvikle software der følger en Microservice arkitektur. 
* Kunne læse, skrive, forstå programdokumentation udvilet gennem swagger, readme filer, docstrings og MkDocs hosted på github pages.  
* Selvstændigt kunne sætte sig ind i brugen af software gennem dets dokumentation 
* Have en forståelse for konceptet Abstraktion inden for softwareudvikling 
* Kende til, og kunne gøre brug af følgende Software designprincipper: SOLID, KISS, DRY og GRASP 
* Kunne bruge et pythonic udviklingsmiljø herunder scriptfiler, interpretor og jupyter notebooks  
* Kunne udvikle egne applikationer/api´er der interagerer med 3. parts apllikationer/api´er 
* Kunne arbejde med en Sqlite relationel database 
* Kunne bruge python som programmeringssprog 



Læringsmålene (Cloud)
---------------------

* Kunne bruge Azure Cloud Platform gennem https://portal.azure.com  
* Have en grundlæggende forståelse for Linux og kunne arbejde med en linux maskine gennem terminalen. 
* Have viden om forskelle og ligheder ved Iaas, Paas, Saas (services) og kunne identificere disse på Azure  
* Have en overordnet forståelse for hvad Github Actions er 
* Forstå grundlæggende Docker koncepter som Image, Container 
* Kunne arbejde med Docker images og Containers gennem Docker Desktop 
* Kunne skrive og forstå docker kommandoer i terminalen som eksempelvis run, build, pull, push, images, ps 
* Kunne forstå og skrive en Dockerfil  
* Forstå sammenhængen i en CI/CD situation mellem Github, Azure Web App og Docker Hub  
* Lave prisberegninger via Azure Prisberegner for anvendelse af cloud-teknologi til idriftsættelse af en konkret applikation og formidle prisberegninger til interessenter. 
* Kunne udvikle microservices vha. Docker og cloud teknologier 



Listen af sider herunder og i venstre side, svare til de lektioner vi kommer til at have gennem dette semester.



.. toctree::
   :maxdepth: 2
   :numbered:  
   
   intro     

   py_intro_1
   py_intro_2
   linux_1
   linux_2
   py_intro_3
   
   introduktion_til_rest_api
   flask
   flask_2
   docker_1
   docker_2

   microservices_1
   microservices_2

   dokumentation   
   swagger

   eksamensprojekt
   auditional_exercises
