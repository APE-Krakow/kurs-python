---
title: "Słowniki"
permalink: /slowniki
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

## Tworzenie słownika (*dictionary*)
Słownik jest tworzony przez podanie dowolnej ilości par klucz-wartość (key-value). Słownik tworzy się za pomocą nawiasów klamrowych lub funkcji `dict()`. Do poszczególnych elementów słownika otrzymujemy dostęp poprzez podanie odpowiedniego klucza w nawiasie kwadratowym. Aby utworzyć nowy wpis w słowniku wystarczy użyć nawiasów kwadratowych i dodać zawartość nowego elementu.

```python
slownik = {"numer": 5, "litera": "a"}
slownik2 = dict(numer=5, nazwa="test")
slownik["slowo"] = "test"

# slownik {"numer": 5, "litera "a", "slowo": "test"}
# slownik2 {"numer": 5, "nazwa": "test"}
```

## Iteracja przez słownik
Aby dokonać iteracji przez słownik, musimy zdefiniować czy chcemy iterować po kluczach (`keys()`), po wartościach (`values()`) czy po parach (`items()`).

```python
for k, v in slownik.items():
    print(f"klucz: {k} wartość: {v}")

for k in slownik.keys():
    print(f"klucz: {k}")

for v in slownik.values():
    print(f"wartość: {v}")
```

## Słowniki składane
Podobnie jak listy, słowniki można tworzyć w momencie ich deklaracji. Aby to zrobić należy użyć tego samego sposobu co przy listach składanych, ale z nawiasami klamrowymi. Należy rozdzielić klucz i wartość słownika dwukropkiem.

```python
# słownik łączący liczby i ich kwadraty
{x: x ** 2 for x in range(10)}
```

## Zbiory (*set*)
Zbiór jest konstrukcją pozwalającą na przechowywanie zestawu elementów. Elementy nie mogą się powtarzać i ich kolejność nie ma znaczenia. Elementów zbioru nie można edytować, ale można je usunąć lub dodać nowe. Zbiory również tworzy się korzystając z nawiasów klamrowych, można też użyć funkcji `set()`.

```python
zbior = {"serce", "mózg", "wątroba", "serce"}
zbior2 = set("nerki", "śledziona", "serce")
# zbior {"serce", "mózg", "wątroba"}
# zbior2 {"nerki", "śledziona", "serce"}
```

Unikalną funkcjonalnością zbiorów jest możliwość odnalezienia części wspólnej lub różnicy za pomocą metod `intersection()` i `difference()`.
Można również sprawdzić czy dany zbiór jest podzbiorem (`issubset()`), nadzbiorem (`issuperset()`), czy może zbiorem rozłącznym (`isdisjoint()`) innego zbioru.

```python
czesc_wspolna = zbior.intersection(zbior2)
print(czesc_wspolna) # "serce"
print(zbior.isdisjoint(zbior2)) # False
```

## Powtórzenie

Nazwa | Znak | Polecenie | Edytowalne | Powtarzalne | Uporządkowane
---|---|---|---|---|---
Lista | [] | `list()` | ✓ | ✓ | ✓
Krotka | () | `tuple()` | × | ✓ | ✓
Słownik | {} | `dict()` | ✓ | ×| ×
Zbiór | {} | `set()` | × | × | ×

## Zadania:
### Pizzeria:
1. Stwórz słownik zawierający listę składników na pizzę i ilość tych składników w zapasie.
2. Stwórz program zadający pytanie użytkownikowi na temat każdego składnika którego pozostaje przynajmniej jedna sztuka w magazynie, a jeżeli użytkownik chce go mieć na pizzy to zmniejsza jego ilość w magazynie.
3. Dodaj opcję aby to użytkownik wpisywał nazwy składników jakie chce umieścić na pizzy, i na tej podstawie będą one usuwane z magazynu.

### Lotniska
Stwórz program analizujący lotniska światowe. W tym celu:
1. Wczytaj dane na temat lotnisk dostarczone z tym zadaniem.
2. Przetwórz je na słownik grupujący nazwy lotnisk z liczbą pasów startowych które posiadają (liczba pasów powinna być kluczem).

```python
pasy_startowe = [("Warszawa", 2),
                 ("Wiedeń", 2),
                 ("Frankfurt", 4),
                 ("Londyn", 2),
                 ("Madryt", 4),
                 ("Radom", 1)]
```

### Ćwiczenia ze słowników składanych:
Za pomocą słowników składanych rozwiąż następujące zadania:
1. Stwórz słownik łączący słowo z liczbą jego wystąpień w tekście. (Generator tekstu: [Lorem Ipsum](https://www.lipsum.com/))
2. Dla listy osób zatrudnionych w firmie, przypisz każdej osobie domyślną wypłatę podaną przez użytkownika.

### System polecania filmów
Na pewnym portalu użytkownicy mogą oceniać filmy w skali od 1 do 5. Na podstawie tych ocen chcemy tworzyć rekomendacje filmów. Uważamy, że dwóch użytkowników ma podobny gust filmowy, jeśli obaj ocenili ten sam film na 4 lub 5.

Film należy polecić użytkownikowi jeśli:
- Nie ocenił jeszcze danego filmu
- Użytkownik o podobnym guście ocenił film na 4 lub 5

Stwórz program który poleci filmy wybranemu użytkownikowi.

Proponowany zbiór danych:

```python
{"Marcin": {"Challengers": 5, "Diuna": 3, "Incepcja": 3, "Avatar": 4, "Matrix": 4, "Pianista": 5, "Batman": 2, "Prestiż": 5},
"Ania": {"Avatar": 2, "Matrix": 2, "Shrek": 5, "Titanic": 4, "Incepcja": 3},
"Wojtek": {"Avatar": 1, "Incepcja": 4, "Lśnienie": 3, "Prestiż": 2, "Interstellar": 4, "Kiler": 5},
"Julia": {"Matrix": 2, "Shrek": 1, "Titanic": 3, "Incepcja": 4, "Batman": 5, "Interstellar": 2, "Kiler": 5, "Challengers": 5},
"Marcel": {"Matrix": 2, "Incepcja": 5},
"Kasia": {"Avatar": 3, "Matrix": 4, "Shrek": 5, "Titanic": 5, "Lśnienie": 5, "Prestiż": 5, "Incepcja": 3, "Batman": 4, "Interstellar": 4, "Kiler": 4, "Challengers": 2, "Diuna": 3}}
```

