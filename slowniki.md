---
title: "Słowniki"
permalink: /slowniki
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

<https://docs.python.org/3/library/stdtypes.html#mapping-types-dict>

## Tworzenie słownika (*dictionary*)
Słownik tworzony jest przez podanie dowolnej ilości par klucz-wartość (key-value). Słownik tworzy się za pomocą nawiasów klamrowych. Do poszczególnych elementów słownika otrzymujemy dostęp poprzez podanie odpowiedniego klucza w nawiasie kwadratowym. Aby utworzyć nowy wpis w słowniku wystarczy użyć nawiasów kwadratowych i dodać zawartość nowego elementu.

```python
slownik = {"numer": 5, "litera": "a"}
slownik["slowo"] = "test"

# slownik {"numer": 5, "litera "a", "slowo": "test"}
```

## Iteracja przez słownik
Aby dokonać iteracji przez słownik, musimy zdefiniować czy chcemy iterować po kluczach (`keys()`), po wartościach (`values()`) czy po parach (`items()`).

```python
for key, value in slownik.items():
    print(f"klucz: {key} wartość: {value}")

for k in slownik.keys():
    print(f"klucz: {key}")

for v in slownik.values():
    print(f"wartość: {value}")
```

## Metody słowników
Słowniki, podobnie jak listy, zawierają dużo wbudowanych metod pozawalających usprawnić prace. Są to: `clear()`, `copy()`, `get()`, `items()`, `keys()`, `pop()`, `popitem()`, `setdefault()`, `update()`, `values()`.
Ich działanie również można znaleźc w dokumentacji.

## Słowniki składane
Podobnie jak listy, słowniki można tworzyć w momencie ich deklaracji. Aby to zrobić należy użyć tego samego sposobu co przy listach składanych, ale z nawiasami klamrowymi. Należy rozdzielić klucz i wartość słownika dwukropkiem.

```python
# słownik łączący liczby i ich kwadraty
{x: x**2 for x in range(10)}
```

## Zbiory (*set*)
Zbiór jest konstrukcją pozwalającą na przechowywanie zestawu elementów. Elementy nie mogą się powtarzać i ich kolejność nie ma znaczenia. Elementów zbioru nie można edytować, ale można je usunąć lub dodać nowe. Zbiory również tworzy się korzystając z nawiasów klamrowych.

```python
zbior = {"serce", "mózg", "wątroba", "serce"}

# zbior {"serce", "mózg", "wątroba"}
```

Unikalną funkcjonalnością zbiorów jest możliwość odnalezienia części wspólnej lub różnicy za pomocą metod `intersection()` i `difference()` lub `symmetric_difference()`.
Można również sprawdzić czy dany zbiór jest podzbiorem (`issubset()`), nadzbiorem (`issuperset()`), czy może zbiorem rozłącznym (`isdisjoint()`) innego zbioru.

Dodatkowo zbiory pozwalają na inne operacje: `add()`, `remove()`, `discard()`, `pop()`, `clear()`, `update()`.

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

## Ćwiczenia
1. Stwórz przykładowy słownik z ucznimi i ocenami, dodaj do niego nowego ucznia, usuń jakiegoś ucznia i innemu zmień ocenę.
2. Przećwicz użycie jednej z zaawansowanych metod opisanych w dokumentacji.

## Zadania:
### Pizzeria:
1. Stwórz słownik zawierający listę składników na pizzę i ilość tych składników w zapasie.
2. Stwórz program zadający pytanie użytkownikowi na temat każdego składnika którego pozostaje przynajmniej jedna sztuka w magazynie, a jeżeli użytkownik chce go mieć na pizzy to zmniejsza jego ilość w magazynie.
3. Dodaj opcję aby to użytkownik wpisywał nazwy składników jakie chce umieścić na pizzy, i na tej podstawie będą one usuwane z magazynu. Jeżeli danego składnika już nie ma, wyświetl odpowiedni komunikat.

### Ćwiczenia ze słowników składanych:
Za pomocą słowników składanych rozwiąż następujące zadania:
1. Stwórz słownik łączący litery z liczbą ich wystąpień w tekście. (Generator tekstu: [Lorem Ipsum](https://www.lipsum.com/))
2. Dla listy osób zatrudnionych w firmie, przypisz każdej osobie domyślną wypłatę podaną przez użytkownika.
3. Przekształć listę produktów i ich cen na słownik zawierający każdy produkt i jego cenę.

```python
[("chleb", 5.50),
("pasta", 12.50),
("mleko", 4.50),
("kwiaty", 12),
("pomidor", 5.20)]
```

### Lotniska
Stwórz program analizujący lotniska światowe. W tym celu:
1. Wczytaj dane na temat lotnisk dostarczone z tym zadaniem (zawiera on nazwę lotniska, jego kod, państwo i długość pasa startowego).
2. Przetwórz je na słownik grupujący nazwy lotnisk z długością jego pasa startowego.
3. Znajdź średnią długość pasa startowego, i nazwę lotniska którego pas ma długość najbliżej średniej.

```python
[
    ("Hartsfield-Jackson Atlanta International Airport", "KATL", "United States", "Atlanta", 3962),
    ("Beijing Capital International Airport", "ZBAA", "China", "Beijing", 3800),
    ("Dubai International Airport", "OMDB", "United Arab Emirates", "Dubai", 4000),
    ("Tokyo Haneda Airport", "RJTT", "Japan", "Tokyo", 3000),
    ("Los Angeles International Airport", "KLAX", "United States", "Los Angeles", 3682),
    ("Heathrow Airport", "EGLL", "United Kingdom", "London", 3660),
    ("Charles de Gaulle Airport", "LFPG", "France", "Paris", 4200),
    ("Sydney Kingsford Smith Airport", "YSSY", "Australia", "Sydney", 3962),
    ("São Paulo-Guarulhos International Airport", "SBGR", "Brazil", "São Paulo", 3700),
    ("Frankfurt Airport", "EDDF", "Germany", "Frankfurt", 4000),
    ("Indira Gandhi International Airport", "VIDP", "India", "Delhi", 4430),
    ("O'Hare International Airport", "KORD", "United States", "Chicago", 3962),
    ("Madrid-Barajas Adolfo Suárez Airport", "LEMD", "Spain", "Madrid", 3500),
    ("Singapore Changi Airport", "WSSS", "Singapore", "Singapore", 4000),
    ("Incheon International Airport", "RKSI", "South Korea", "Seoul", 3750)
]
```

### Licznik plików
Stwórz program który policzy różne rodzaje plików znajdujące się w podanym przez ciebie katalogu. Poniżej zamieszczono kod programu który wygeneruje listę plików. Wklej go na początku programu:

```python
import os

def get_file_names_from_directory(directory):
    try:
        # List all files in the specified directory
        files = [f for f in os.listdir(directory) if os.path.isfile(os.path.join(directory, f))]
        return files
    except FileNotFoundError:
        print("Taki katalog nie istnieje")
        return []
    except PermissionError:
        print("Nie masz uprawnień aby otworzyć ten katalog")
        return []
```

Następnie użyj następujących instrukcji aby uzyskać listę plików:
```python
# Example usage
directory_path = input("Podaj ścieżkę do katalogu który będzie przeskanowany: ")
file_names = get_file_names_from_directory(directory_path)
```
Następnie stwórz słownik który pogrupuje pliki według ich rozszerzenia, np. mp3, mp4, pdf, txt, py i tak dalej. Na końcu wypisz raport który podsumuje ile plików danego typu znajdowało się w katalogu.

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

