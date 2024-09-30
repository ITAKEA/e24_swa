# Docker II
Idag skal vi arbejde videre med docker.     
Vi skal kigge på environement variabler, både på jeres egne computere og i jeres docker images og containers.    
Vi skal desuden kigge på hvordan vi kan arbejde med persistent data (data som ikke forsvinder ved en update af feks. et image).
I skal desuden kunne pushe jeres images til dockerhub.    

OBS: Til jer der ikke var der i fredags: sørg for at forstå materialet og øvelserne fra [docker 1 dagen](https://itakea.github.io/e24_swa/docker_1.html).  

## Læringsmål
* Kunne bruge environement variables sammen med docker images og containers.
* Kunne forstå hvad et docker volume er og hvad det kan bruges til.
* Kunne pushe images til DockerHub.

## Forberedelse
1. Sørg for at have lavet øvelserne fra i fredags. 
2. [Opret en konto på DockerHub](https://hub.docker.com/)
3. [Skim denne 'Dockerfile reference' igennem](https://docs.docker.com/reference/dockerfile/)
4. [Kig på dette docker Cheatsheet fra sidst, og under dag 2 for de ting vi skal arbejde med i dag](materialer/docker_cheatsheet.md)
5. Undersøg hvad "Environment Variabler" er.
6. Undersøg hvordan man arbejder med "Persistance Data" i et docker image.
7. [Læs afsnittet "Where to Store Data" i denne documentation](https://hub.docker.com/_/mysql/)   


## Dagens indhold
* Recap fra sidst
    * -it, -p 
    * --rm, -d 
    * pip freeze -> requirements.txt
    * docker Image
        * docker build

* Vi kigger herefter på: 
    * environment variabler
    * Dev vs. prod environemnet
    * persistens og docker volumes
    * Dele images på DockerHub

Vi bruger denne kode som udgangspunkt for dagen: [Kode fra undervisningen](https://github.com/ITAKEA/kode_fra_undervisning_e24/tree/master/docker)

## Materialer
* [Opret en konto på DockerHub](https://hub.docker.com/)
* [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
* [Docker Cheatshee](materialer/docker_cheatsheet.md)
* [Læs afsnittet "Where to Store Data" i denne documentation](https://hub.docker.com/_/mysql/)   
* [Kode fra undervisningen](https://github.com/ITAKEA/kode_fra_undervisning_e24/tree/master/docker)

### Øvelser

#### Øv 1: mysql container med persistent data (volume)
Med denne run kommando som udgangspunkt skal du starte en Mysql container

`docker run  --name some-mysql -v /my/own/datadir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql`   

* Du skal ændre `/my/own/datadir` til noget der passer med mappestrukturen på din computer.
* Du skal sørge for at have terminal adgang til containeren.   
* Du skal sørge for at container slettes når den lukkes.
* Du skal sørge for at have åbnet port 3306 til containeren.
* Du kan evt. ændre password.

* Når alt fungerer skal du åbene Mysql Workbench, eller en tilsvarende GUI og forbinde til Mysql Containeren. 
* Du skal lave en database, en tabel og indsætte lidt data.
* Herefter skal du slukke din container.

Kør herefter en ny container med run kommandoen, forbind til den, og se at din database, tabel og data stadig er der.
    

#### Øv 2: Gem din database i /home/data
