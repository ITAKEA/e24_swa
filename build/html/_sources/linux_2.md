# Linux OS II

## Forberedelse
I skal se denne 5 minutters video om text editoren nano:
* [Nano Text Editor Basics (pico) - How to Use Nano on Linux](https://www.youtube.com/watch?v=Jf0ZJZJ8jlI) 

herefter må i gerne gå i gang med denne video.     
Det er ikke super vigtigt at i er nået igennem det hele inden undervisningen, da der bliver tid til det i selve undervisningstimerne også. 

* [Lecture 1: Course Overview + The Shell (2020)](https://www.youtube.com/watch?v=Z56Jmr9Z34Q) (noget af det manden snakker om har i været igennem, noget har i ikke) 

## Dagens indhold
Undervinsingen i dag er online via Teams. I kan finde et link til rummet på Fronter. 

Jeg holder en kort introduktion til hvad i skal lave i dag, herefter står den på Video, øvelser og hjælp fra mig.

## Hjemmearbejde
Hvis i ikke er blevet færdige, skal i lave øvelserne færdige efter timerne. 

## Materialer

* [Nano Text Editor Basics (pico) - How to Use Nano on Linux](https://www.youtube.com/watch?v=Jf0ZJZJ8jlI)
* [Lecture 1: Course Overview + The Shell (2020)](https://www.youtube.com/watch?v=Z56Jmr9Z34Q) (noget af det manden snakker om har i været igennem, noget har i ikke) 

### Øvelser

#### Øvelse 1: Missing Semester
Øvelserne herunder og den video i har set inden idag er taget fra MIT kurset [Missing Semester](https://missing.csail.mit.edu/2020/course-shell/) 
Nogle af øvelserne er "gør dette" og andre øvelser er mere en opfordring til at undersøge emnet.     
Der er refereret til `man` i øvelserne. Det virker ikke på jeres linux maskine, det fungere til gengæld fint i en Google søgning eller en LLM. Så bare skriv feks. `man touch`, eller `man chmod` for at bruge `man` kommandoen. 

1. Create a new directory called `missing` under `/tmp`.
1. Look up the `touch` program. The `man` program is your friend.
1. Use `touch` to create a new file called `semester` in `missing`.
1. Write the following into that file, one line at a time:
    ```
    #!/bin/sh
    curl --head --silent https://missing.csail.mit.edu
    ```
    The first line might be tricky to get working. It's helpful to know that
    `#` starts a comment in Bash, and `!` has a special meaning even within
    double-quoted (`"`) strings. Bash treats single-quoted strings (`'`)
    differently: they will do the trick in this case. See the Bash
    [quoting](https://www.gnu.org/software/bash/manual/html_node/Quoting.html)
    manual page for more information.
 1. Try to execute the file, i.e. type the path to the script (`./semester`)
    into your shell and press enter. Understand why it doesn't work by
    consulting the output of `ls` (hint: look at the permission bits of the
    file).
 1. Run the command by explicitly starting the `sh` interpreter, and giving it
    the file `semester` as the first argument, i.e. `sh semester`. Why does
    this work, while `./semester` didn't?
 1. Look up the `chmod` program (e.g. use `man chmod`).
 1. Use `chmod` to make it possible to run the command `./semester` rather than
    having to type `sh semester`. How does your shell know that the file is
    supposed to be interpreted using `sh`? See this page on the
    [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)) line for more
    information.
 1. Use `|` and `>` to write the "last modified" date output by
    `semester` into a file called `last-modified.txt` in your home
    directory.


#### Øvelse 2: lav dit eget Commandline program i python

I denne øvelse skal du lave dit eget program, skrevet i python og eksekveret fra din Kommandolinie på samme måde som `ls`, `cd` etc.    
Du kender programmer som `ls`, `cd`, `pwd`, `tree` osv. og vi har set hvor henne på din linux computer de er placeret (feks. `/bin/ mappen`).     
Dit program skal kunne eksekveres på samme måde.

I den tidligere øvelse lavede du et `bash script` (pkt. 4), og du gjorde det eksekverbart med den første linie `#!/bin/sh`.     
Python script kan gøres eksekverbare på samme måde, i stedet for stien til hvor `sh` er instaleret på maskinen, skal du skrive stien til hvor `python3` er installeret.

Hvad programmet konkret skal gøre bestemmer du selv.    

Når du er færdig med dit script og du har fået det til at virke, skal du `push` é det til github og lave en installationsvejledning i dets readmefile, og aflevere et link til repositoriet på [Fronter](https://kea-fronter.itslearning.com/plans/courses/6741/plan/106947/element/1298786?BackDestination=0&BackData=%7B%22BackDestination%22%3A%220%22%7D&planner2-sb-collapsed=false).    
Så kigger vi på nogle af jeres programmer på fredag.     
Når du aflevere må du gerne skrive hvis jeg må vise det i klassen. Hvis du ikke skriver noget regner jeg med at du helst vil være fri.

