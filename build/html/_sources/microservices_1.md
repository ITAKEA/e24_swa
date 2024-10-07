# Microservices 1

![](_static/img/microsevices_quote.png)

## Forberedels

Se de 2 videoer og læs artiklen:    
* [Video: What are Microservices?](https://www.youtube.com/watch?v=CdBtNQZH8a4) (6:37)
* [Microservices (Martin Fowler)](https://martinfowler.com/articles/microservices.html) (30:00)   

## Læringsmål
* Have viden om grundprincipperne i hvad en Microservice arkitektur er
* Kunne bygge microservices der arbejder sammen gennem et JSON API
* Kunne forstå konceptet om et API GATEWAY

## Dagens indhold

Vi starter dagen med en gennemgang af hvordan i kan vha. environment variabler, docker volumens kan opnå persistens på tværs af jeres docker images og containers. (det som vi skulle have lavet sidste onsdag).

Herefter laver vi en services fra øvelsen herunder sammen ved tavlen, og i fortsætter i grupper med øvelsen herunder. 

## Materialer

* [Query parametre](materialer/routes.md)
* [Video: What are Microservices?](https://www.youtube.com/watch?v=CdBtNQZH8a4) (6:37)
* [Microservices (Martin Fowler)](https://martinfowler.com/articles/microservices.html)



<!--
Todo: Lav en tutorial og video baseret på denne artikkel, men med Azure som host
* [How To Build and Deploy Microservices With Python](https://kinsta.com/blog/python-microservices/)

## flask-change-microservice

* [Building a Realistic Microservice Step-By-Step with Flask](https://www.youtube.com/watch?v=QauGyIdGiNc)
* [flask-change-microservice](https://github.com/noahgift/flask-change-microservice/tree/main)

-->



### Øvelser
#### Shopping Site Microservices
Listen herunder indeholder nogle forslag til hvad en online markedsplads, som feks. Amazon.com kunne indeholde af Microservices.    
Vi har sammen lavet XXX og I skal nu lave 2 stykker yderligere plus et API GATEWAY.    

I forhold til Product Catalog Service (hvis i laver den) kan i med fordel bruge data fra dette [api](https://dummyjson.com/docs)    
 
Husk at jeres services så vidt det er muligt skal kunne fungere uden de andre services. Ikke nødvendigvis perfekt, men men dog godt nok til at de stadig kan bruges uden at være afhængig af de andre services.

**Docker**
Jeres services skal kunne køre i hver deres docker container, og i skal gøre brug af environment variabler hvor det giver mening. I skal også sørge for at jeres images kan arbejde med persistent data via volumes.    

**Grupper**
Det vil være meget fint hvis i arbejder sammen i grupper og hver gruppe står for én Service af det samlede system. Det i skal være enige om inden i satrter er endpoints på jeres api´er. Altså hvad kan jeres service bruges til?

I skal i README filerne til alle Services beskrive jeres endpoints.

I skal udover jeres services herunder have et API GATEWAY.  
 
Sørg for at lave jeres services simple og kun med de nødvendige funktionaliteter (KISS).     

1. **User Service**:
   - Håndterer brugerkonti, herunder registrering, autentificering og profiladministration.
   - Behandler login, logout, passwordhåndtering og brugerroller.

2. **Product Catalog Service**:
   - Styrer listen over tilgængelige produkter, inklusive detaljer såsom navn, beskrivelse, pris og billeder.
   - Tilbyder funktionalitet til at søge, filtrere og kategorisere produkter.

3. **Inventory Service**:
   - Håndterer lagerbeholdningen for produkter.
   - Sporer ændringer i lageret (f.eks. justeringer af mængden efter salg).

4. **Order Service**:
   - Håndterer ordreplacering, behandling og sporing.
   - Administrerer livscyklussen for en ordre fra oprettelse til opfyldelse.

5. **Payment Service**:
   - Behandler betalinger for ordrer.
   - Integrerer med betalingsgateways og styrer transaktionsregistre.

6. **Cart Service**:
   - Håndterer brugernes indkøbskurve.
   - Tilbyder funktioner til at tilføje, fjerne og opdatere varer i kurven.

7. **Shipping Service**:
   - Beregner forsendelsesomkostninger og styrer leveringsmuligheder.
   - Sporer forsendelser og opdaterer ordrestatus ved levering.

7. **Currency Service**:
   - Håndterer omregning mellem forskellige valutaer for at sikre, at priserne vises korrekt afhængigt af brugerens valgte valuta.
   - Opdaterer valutakurser i realtid ved at integrere med eksterne valutakurseressourcer og API'er.
   - Giver funktionalitet til at indstille eller vælge en foretrukken valuta for både brugere og administratorer.

8. **Review and Ratings Service**:
   - Giver brugerne mulighed for at anmelde og vurdere produkter.
   - Styrer moderation og visning af brugergenereret indhold.

9. **Notification Service**:
   - Sender meddelelser til brugerne (f.eks. ordrebekræftelser, forsendelsesopdateringer).
   - Kan håndtere forskellige kanaler som e-mail, SMS eller push-beskeder.

10. **Search Service**:
    - Tilbyder fuldtekstsøgning på tværs af produkter.
    - Implementerer funktioner som auto-forslag og forudsigende søgning.

11. **Analytics Service**:
    - Samler og behandler data til rapportering og indsigt.
    - Tilbyder dashboards og metrikker for salg, brugeradfærd osv.

12. **Recommendation Service**:
    - Foreslår produkter til brugerne baseret på deres adfærd og præferencer.
    - Implementeres ved hjælp af algoritmer som samarbejdsfiltrering eller indholdsbaseret filtrering.




