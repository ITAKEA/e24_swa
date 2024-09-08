# Linux OS
Formålet med dagens emne er at du bliver fortrolig med at bruge Linux. Det er en lejeplads og jo mere du leger des bedre er det!


## Læringsmål
* Installere Docker Desktop på din computer
* Installere Linux gennem Docker på din computer
* Få en overordnet forståelse af conceptet "Virtuel Computer"
* Bruge terminalen i Linux
* Få et praktisk overblik over de hyppigst brugte shell kommandoer.
* Forstå Linux´s fil og mappestruktur.
* Kunne installere applikationer i dit linux system.
* Forstå hvad en package manager er og gør.
* Kunne bruge en terminal baseret texteditor (nano)
* Kunne eksevere applikationer (python programmer) på din linux computer

## Forberedelse
(1 time)

* Installer det software vi skal bruge i undervisningen: [Installationer](https://techkea.github.io/f23/materialer/installationer_f24.html)

Herefter se og følg følgende tutorials:

* [Linux for Hackers // EP 1 (11:32)](https://www.youtube.com/watch?v=VbEx7B_PTOE&list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL)
* [the Linux File System explained in 1,233 seconds // Linux for Hackers // EP 2 (20:32)](https://www.youtube.com/watch?v=A3G-3hp88mo&list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL&index=2)

(jeg har (lidt sent) fjernet den 3. video da den ikke er mega relevant lige nu. Hvis i gerne vil se den alligevel eller gense den er der et link i slutningen af video nummer 2).
<!-- * [HELP!! (for when you suck at Linux) // Linux for Hackers // EP3 (13:13)](https://www.youtube.com/watch?v=Y17KTiJLcyQ&list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL&index=3) -->


## Dagens indhold
I dag skal i lære at finde rundt i Linux styrresystemet.

Vi kommer til at lege med systemet blandt andet igennem at bruge disse kommandoer: [Linux terminal commands and file system](https://techkea.github.io/f23/materialer/unix_commands.html)

Herefter laver vi øvelsene herunder.


## Øvelser
**Alle øvelser skal laves på jeres Linux maskine**    

### Øv1: Slet din Linux container
Inden i går i gang med disse øvelser skal i slette jeres Linux container, og tømme webtop/ mappen, og køre docker run kommaondoen igen.     

```` docker run -d --name=webtop-ubuntu-mate --security-opt seccomp=unconfined  -e PUID=1000 -e PGID=1000 -e TZ=Etc/UTC -e SUBFOLDER=/  -e TITLE=Teknologi  -p 3000:3000 -p 3001:3001 -v ~/webtop:/config -v /var/run/docker.sock:/var/run/docker.sock  --shm-size="1gb"  --restart unless-stopped lscr.io/linuxserver/webtop:ubuntu-mate  ````


### Øv2: Klon og arbejd med undervisningsrepositoriet
I denne øvelse skal I klone dette repository: https://github.com/ITAKEA/kode_fra_undervisning_e24.git.    
Herefter skal I få det hele til at virke på jeres Linux-maskine, ligesom I fik det til at virke på jeres egen computer første gang, vi havde undervisning.

Der er nogle enkelte regler, I skal følge:

* I må ikke arbejde direkte i master-branchen.
* I skal ikke bruge VSCode eller nogen anden editor.
* I skal åbne og redigere notebook-filerne i jeres browser. Det kan I gøre ved at bruge kommandoen ```jupyter-notebook```, som åbner den mappe, I befinder jer i, i et browser-vindue.
* For at kunne bruge denne kommando skal Jupyter installeres i din Python-installation.
* Det gør I med kommandoen ```pip install jupyter``` (mere om pip-kommandoen næste gang).

### Øv3: Unix command øvelser
* [Øvelse: Unix Command Exercises](https://github.com/ITAKEA/kode_fra_undervisning_e24/blob/master/linux1/exercises/unix_commands_exercises.md) - [løsning](https://github.com/ITAKEA/kode_fra_undervisning_e24/blob/master/linux1/exercises/solution/unix_ex_solutions.md)





