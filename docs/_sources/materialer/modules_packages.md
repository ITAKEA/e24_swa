# Modules og Packages

## Hvad er et Modul?
Et modul i Python er en fil, der indeholder Python-kode, og som ender med filtypenavnet .py.

Så ```script.py``` er et modul.

## Hvad er en Package?
En package i Python er i bund og grund en mappe, der bruges til at organisere relaterede moduler (.py-filer).     

Så en mappe ```calculate``` der indeholder .py filer er en package.

```
calculate
    ├── equations.py
    ├── geometry.py
    ├── script.py
    └── tensors.py

```

## Import af moduler og packages
Når du skal importere et modul, eller en pakke kan det gøres på følgende måder:


### Moduler

Hvis du har en python fil (module) der ser sådan ud

```
# script.py

def add(a,b):
    return a + b

```
Så importeres og bruges dette på følgende måde:

```
    import script

    script.add(1,2)

```
Det er desuden muligt at importere mere specifikt:

```
    from script import add

    add(1, 2)

```

### Packages


Hvis du har en package der ser sådan ud:

```
calculate
    ├── equations.py
    ├── geometry.py
    ├── script.py
    └── tensors.py

```


Så importeres og bruges dette på følgende måde:

```
    import calculate

    calculate.script.add(1,2)

```
Det er desuden muligt at importere mere specifikt:

```
    from calculate.script import add

    add(1, 2)

```
