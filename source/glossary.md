# Ordliste og begreber


## DRY
Don´t repeat yourself.    


## Coupling
Coupling beskriver graden af **afhængighed** mellem forskellige moduler, klasser eller services etc. i et software system.     
Lav coupling (eller "loose coupling") er ofte målet, da det indikerer, at hver service er relativt uafhængig af de andre, hvilket gør systemet lettere at modificere, teste og forstå.

Eksempel:
Hvis en Service, UserProfile, kan ændre sin interne implementering uden at påvirke en anden service  UserInterface, som bruger UserProfile, siger vi, at der er lav coupling mellem disse to services.

## Cohesion
Cohesion refererer til graden af, hvor tæt **relaterede** og **fokuserede** ansvarsområderne af et enkelt modul, klasse eller service etc. er.     
En høj grad af cohesion indikerer, at elementerne inden for en service er stærkt relaterede til hinanden, hvilket gør det lettere at forstå, teste og vedligeholde.     
Cohesion er en ønskværdig egenskab i software, fordi det fremmer isoleringen af funktionalitet og mindsker kompleksiteten.

Eksempel:    
En Service, EmailSender, der har functioner til at formatere og sende e-mails har høj cohesion, da alle dens funktioner er fokuseret på email-relaterede aktiviteter.

## First class functions
At en funktion er en førsteklasses funktion betyder, at de kan tage andre funktioner som parametre, og at de kan returnere funktioner.   

Et eksempel på dette:

```
    def func(x):
        return x

    y = func(len)
    y('Hello') # Output er 5
```


## Inner functions

## KISS

## OOP

Objektorienteret programmering (OOP) er et programmeringsparadigme. Et objekt kan indeholde attributter, der gemmer dets data, og metoder som udføre dets handlinger.

```
    class Person:
        def __init__(self, name):
            self.name = name   # en attribut som indeholder data

        def 

```

Objekter har en tilstand som er beskrevet i dets attributter, og det kan udføre handlinger gennem dets metoder.

Attributter er beskrevet vha. navneord, og handlinger med udsagnsord.

Hvis du har behov for at gemme en tilstand, er OOP ofte den rette programeringsparadigme.

I python er objekter baseret på klasser. Og fra disse klasser laver man et objekt. 

Et objekts tilstand (dets attributter og deres værdier) kan aflæses ved at skrive:

```
    obj.__dict__
```
Dets metoder (handlemuligheder) kan findes ved:

```
    dir(obj)
```



## Pure function
En "ren funktion" er en funktion, der for ethvert givet input altid producerer det samme output og ikke har nogen observerbare sideeffekter i applikationen eller systemet.

At en funktion er "ren" eller "pure" refererer til et bestemt koncept inden for programmering, specifikt i funktionel programmering. En ren funktion er en type funktion der opfylder to hovedkriterier:

* **Determinisme:** En ren funktion returnerer altid det samme resultat givet de samme input. Det betyder, at funktionens output udelukkende er bestemt af dens input, uden nogen ekstern påvirkning fra statens ændringer eller sideeffekter.
* **Ingen sideeffekter:** En ren funktion forårsager ingen sideeffekter i systemet. Det betyder, at den ikke ændrer nogen tilstande uden for dens scope eller påvirker omverdenen (f.eks. modificering af globale variabler, skrivning til databaser eller filsystemer, osv.).
Her er hvordan man kan formulere princippet om en ren funktion:

Et eksempel på en ren function:

```
    def add(a, b):
        return a + b

    add(5, 3) # Output vil altid være 8
```

Et eksempel på en ikke ren function:

```
    counter = 0  # Global variabel

    def increment(value):
        global counter
        counter += value
        return counter

    increment(5)  # Output: 5
    increment(5)  # Output: 10
```
