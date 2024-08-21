# Python - Datastrukture

I dag skal vi arbejde med pythons datastrukturer. Python har som udgangspunkt kun fire indbyggede datastrukture. Det er Lister, Tuples, Sets og Dictionaries.     
Efter i dag vil i være i stand til at oprette  Listes og Tupler, tilgå deres elementer vha. deres index, bruge pythons slicing værktøj på lister og tupler, bruge arethmetikske operatore på lister og tupler, bruge pythons indbyggede functioner på lister og tupler, arbejde med metoderne tilknyttet list og tuple objekterne, og i vil have en grundlæggende forståelse for forskellen i brugen af disse 2.     
I vil kunne bruge Sets til at finde unikke verdier i en collection, og i vil arbejde med Dictionaries og forstå dens key : Value struktur.

## Læringsmål
---        
- Arbejde med lister, tuples
    - Arbejde med deres indeks
    - Bruge slicing/udsnit-syntaksen
- Kende de vigtigste forskelle mellem lister og tuples
- Læse fra filer og skrive til filer ved hjælp af den indbyggede "open" funktion.

## Forberedelse
---
Før vi mødes i klassen skal du have:

* Skimmed denne artikkel: [Lists and Tuples in Python](https://realpython.com/python-lists-tuples/) (15 min)
* Skimmed denne artikkel: [Sets in Python] (https://realpython.com/python-sets/) (15 min)
* Skimmed denne artikkel: [Dictionaries in Python](https://realpython.com/python-dicts/) (15 min)

For at checke om du har den rigtige forståelse skal du lave disse quizes:

* [Python Dictionaries Quiz](https://realpython.com/quizzes/python-dicts/)(15 min)
* [Python Sets Quiz](https://realpython.com/quizzes/python-sets/) (15 min)
* [Python Lists and Tuples Quiz](https://realpython.com/quizzes/python-lists-tuples/) (15 min) 

## Dagens indhold
---
* [Noter list/tuples] (teachings notes from today](notebooks/noterlists_tuples.ipynb)
* [Noter sets/dicts](teachings notes from today](notebooks/notes_set_dicts.ipynb>)
* [Kodeeksempler fra undervisningen](https://github.com/python-elective-kea/spring2024-code-examples-from-teachings/tree/master/ses2)

## Hjemmearbejde
---
* Du skal lave øvelserne herunder færdige. 


## Materialer
---

* [Lists and Tuples in Python](https://realpython.com/python-lists-tuples/)
* [How to Use sorted() and .sort() in Python](https://realpython.com/python-sort/)
* [Notebook list/tuples teachings notes from today](notebooks/noterlists_tuples.ipynb)
* [Noter sets/dicts](teachings notes from today](notebooks/notes_set_dicts.ipynb>)
* [Code examples from teachings](https://github.com/python-elective-kea/spring2024-code-examples-from-teachings/tree/master/ses2)


### Øvelser
---
#### Ex 0.1: Slicing
---
By using the slicing syntax change the following collections.

After slicing:

```
['Hello', 'World', 'Huston', 'we', 'are', 'here'] should become -> ['World', 'Huston', 'we', 'are']
['Hello', 'World', 'Huston', 'we', 'are', 'here'] -> ['Hello', 'World']
['Hello', 'World', 'Huston', 'we', 'are', 'here'] -> ['are', 'here']
['Hello', 'World', 'Huston', 'we', 'are', 'here'] -> ['are']
['Hello', 'World', 'Huston', 'we', 'are', 'here'] -> ['Hello', 'Huston', 'are']
['Hello', 'World', 'Huston', 'we', 'are', 'here'] -> ['here', 'are', 'we', 'Huston', 'World', 'Hello']
('Hello', 'World', 'Huston', 'we', 'are', 'here') should become -> ['World', 'Huston', 'we', 'are']
'Hello World Huston we are here' -> 'World Huston we'
``` 

Figure out more on your own and practice this a lot!    

   <hr>

### Ex 1.1: Is it a tuple or a list?
---
| The following data should be presented as either a list or a tuple, or as a combination of both.    
| Your job is to choose the right one. 
| Hint: A list is a collection of the same type of data, a tuple is a record (e.g. in a database a **record** is called a **row**)

1. Claus, 51, male, clbo@kea.dk, 31011970-1313
2. Bmw, Toyota, Hyundai, Skoda, Fiat, Volvo
3. Claus, Henning, Torben, Carl, Tine
4. 'Hello', 'World', 'Huston', 'we', 'are', 'here'
5. Rolling Stones, Goats Head Soup, 31 August 1973, 46:56
6. 40.730610, -73.935242, New York City, NY, USA; 31.739847, 65.755920, Kandahar, Kandahar Province, Afghanistan;
   
   <hr>

### List & Tuples, Set, Dict exercises
---
* `List & tuple exercises <exercises/lists/lists.rst>`_
* `Set exercises <https://github.com/python-elective-kea/spring2024-code-examples-from-teachings/blob/master/ses2/exercises/sets.py>`_
* `Dict exercises <https://github.com/python-elective-kea/spring2024-code-examples-from-teachings/blob/master/ses2/exercises/dict.py>`_

#### quizes
* `Lists and Tuples Quiz <https://realpython.com/quizzes/python-lists-tuples/>`_
* `"while" Loops Quiz <https://realpython.com/quizzes/python-while-loop/>`_
