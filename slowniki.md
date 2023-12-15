# Słowniki (dictionary)
## Tworzenie słownika
Słownik jest tworzony przez podanie dowolnej ilości par klucz-wartość (key-value). Słownik tworzy się za pomocą nawiasów klamrowych lub funkcji `dict()`. Do poszczególnych elementów słownika otrzymujemy dostęp poprzez podanie odpowiedniego klucza.

```
slownik = {"numer": 5, "litera": "a"}
slownik2 = (numer=5, nazwa="test")
slownik["numer"] == 5
```

## Iteracja przez słownik
Aby dokonać iteracji przez słownik, musimy zdefiniować czy chcemy iterować po kluczach (`keys()`), po wartościach (`values()`) czy po parach (`items()`).

```
for k, v in slownik.items():
    print(f"klucz: {k} wartość: {v}")

for k in slownik.keys():
    print(f"klucz: {k}")

for v in slownik.values():
    print(f"wartość: {v}")
```

## Zbiory (set)
Zbiór jest konstrukcją pozwalającą na przechowywanie zestawu elementów. Elementy nie mogą się powtarzać i ich kolejność nie ma znaczenia. Elementów zbioru nie można edytować, ale można je usunąć lub dodać nowe. Zbiory również tworzy się korzystając z nawiasów klamrowych, można też użyć funkcji `set()`.

```
zbior = {"serce", "mózg", "wątroba"}
zbior2 = set("nerki", "trzustka",  "śledziona")
```

Unikalną funkcjonalnością zbiorów jest możliwość odnalezienia części wspólnej lub różnicy za pomocą metod `intersection()` i `difference()`

## Powtórzenie
Nazwa | Znak | Polecenie | Edytowalne | Powtarzalne | Uporządkowane
---|---|---|---|---|---
Lista | [] | `list()` | ✓ | ✓ | ✓
Krotka | () | `tuple()` | × | ✓ | ✓
Słownik | {} | `dict()` | ✓ | ×| ×
Zestaw | {} | `set()` | × | × | ×

## Zadania:
1. Stwórz słownik zawierający listę składników na pizzę i ilość tych składników w zapasie.
2. Stwórz program zadający pytanie użytkownikowi na temat każdego składnika którego pozostaje przynajmniej jedna sztuka w magazynie, a jeżeli użytkownik chce go mieć na pizzy to zmniejsza jego ilość w magazynie.
3. Stwórz program który 



