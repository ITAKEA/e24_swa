# Docker

## Læringsmål

* Forstå hvad docker er og hvad vi skal bruge det til.
* Have en forståelse for hvad Images, Containers og Dockerfiles er og hvordan de relaterer sig til hinanden.
* Kunne bygge et docker image med `docker build`, og kunne forstå og bruge flags som `--name`
* Kunne køre en docker container med `docker run`, og kunne forstå og bruge flags som `-it -rm -p -d --name --env`
* Kunne skrive og bruge en Dockerfil med kommandoerne `FROM, COPY, WORKDIR, RUN, CMD`    
* Kunne bygge et docker image med `docker build ...`    
* Kunne arbejde med et Github workflow der inkludere en Dockerfil.    

## Forberedels

Se de første ca. 28 minutter af denne video.   
Jeg har sat videoen til at starte 2:26 fra start, da det første ikke er relevant for jer.     
Fra 11:54 til 15:29 snakker manden on installation af docker. Det behøver i ikke at se, da i allerede har Docker installeret.    
De sidste 20 minutter er en introduktion til Linux, og det har vi jo haft.    

* [Docker Tutorial for Beginners](https://youtu.be/pTFZFxd4hOI?feature=shared&t=146) (27:54)

I skal desuden køre disse 2 kommandoer i `gitbash` (windows) eller `terminalen` (Mac)

* `docker pull ubuntu:latest` (Dette downloader et ubuntu linux image til din computer)
* `docker pull nginx:latest` (Dette downloader et nginx webserver image til din computer)

Vi kommer til at bruge det i undervisningen, men for at undgå kø på skolens netværk skal i gøre det inden vi mødes.

## Dagens indhold

* Vi starter med en [quiz]() for at teste jeres forståelse af emnet.
* Herefter snakker vi udfra dette [Docker CheatSheet](materialer/docker_cheatsheet.md)
* Og laver dernæst en Hello World python/docker applikation sammen.
* Og så ... øvelserne herunder. 

## Materialer

* [Docker Tutorial for Beginners](https://youtu.be/pTFZFxd4hOI?feature=shared&t=146) (27:54)
* [Docker CheatSheet](materialer/docker_cheatsheet.md)

### Øvelser

#### Øv 1: Lav en ny startside til din nginx server

Kør kommandoen: `docker run -it --rm -p 8080:80 nginx`    

I vil kunne se hvor html filen er placeret i filsystemet her : https://hub.docker.com/_/nginx   








