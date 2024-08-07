# Softwaretests

## Materialer
* [Testing with Python (part 1): the basics](https://www.bitecode.dev/p/testing-with-python-part-1-the-basics)
* [Testing with Python (part 2): moving to pytest](https://www.bitecode.dev/p/testing-with-python-part-2-moving)


## Øvelser

### Øv 1: Hvilke tests?
I skal skrive de nødvendige tests til dette modul: 
I skal bruge pytest pakken.    

**calc.py**

```
    def add(*args):
        """Calulate the sum of all arguments

    arguments: integer numbers

"""
        return sum(args)
    
```

### Øv 1: Filehåndtering

(Tip: Denne øvelse kan med fordel laves på jeres Linux maskine, da i ellers resikere at slette ting og sager på jeres egen computer)

Som udgangspunkt skal i lave en applikation som kan håndtere filer i en rodmappe og en destinationsmappe. Den skal opfylde følgende regler.

- Hvis en fil findes i roden, men ikke i destinationen, kopier filen over.
- Hvis en fil findes i roden, men den har et andet navn end i destinationen, omdøb destinationsfilen så de matcher.
- Hvis en fil findes i destinationen, men ikke i roden, fjern den.

Nyttige moduler i kan gøre brug af til dette er:

* os, subprocesses, hashlib.

**Tests**

Problemet med en applikation som denne er at man riskere lige pludselig at have slette filer der ikke skulle have været slettet. Det vil vi gerne undgå og derfor skal vi lave nogle tests der kan sørge for at det ikke sker.

1. Start med at lave en beskrivelse der lister hvad der er vi gerne vil sikre os med vores tests
2. Skriv herefter jeres tests og gør brug af **pytest** modulet.



---


* [Python's unittest: Writing Unit Tests for Your Code Quiz](https://realpython.com/quizzes/python-unittest/)
* [Write Unit Tests for Your Python Code With ChatGPT](https://realpython.com/chatgpt-unit-tests-python/)
* [Unit test]()


* [Testing with Python (part 1): the basics](https://www.bitecode.dev/p/testing-with-python-part-1-the-basics)
* [Testing with Python (part 5): the different types of tests](https://www.bitecode.dev/p/testing-with-python-part-5-the-different)
