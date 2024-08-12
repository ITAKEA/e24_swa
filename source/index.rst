SoftwareArkitektur ITA 3. semester
==================================

Materialet på denne side er kompendiet til faget Softwarearkitektur på ITA uddannelsens 3. semester på KEA.  

Læringsmålene  
-------------
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

* Unittests

Det overordnede arkitektoniske rammeværktøj på dette semester bliver **Microservices**.     
Microservices er som ordet hendtyder små programmer (services) der hver især tager sig af en lille del af den samlede helhed et system skal udføre.     
Hver service tager imod input og leverer et output gennem et restfull API, og hver service er deployet i en Docker Container. 

For at dette kommer til at fungerer skal i lære at bruge et Web Framework der hedder 

* Flask 
  
og som i vores tilfælde leverer API endpoints.

Vi skal desuden kigge på brugen af en 

* Object Relational Mapper (ORM) 

som gør os i stand til at interageremed  en database gennem software objekter i stdet for sql queries.     
En ORM gør det desuden nemt at skifte database uden at skulle ændre markant i sin kode, og er derved med til at gøre vores service mere skalerbare. 


De samlede læringsmål for hele semesteret i Softwarearkitektur er:


Listen af sider herunder og i venstre side, svare til de lektioner vi kommer til at have gennem dette semester.



.. toctree::
   :maxdepth: 2
   :numbered:  
   
   intro     

   py_intro_1
   py_intro_2
   py_intro_4
   py_intro_3


   introduktion_til_rest_api
   flask
   flask_2
   decorators
   oop_1

   orm
   
   test_1
   dokumentation
   dag1
   swagger
   16 
   eksamensprojekt
   auditional_exercises
