---
title: "Listy (list)"
permalink: /listy
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

<https://docs.python.org/3/library/stdtypes.html#list>

## Tworzenie list

Za pomocą listy można stworzyć jedną zmienną przechowującą wiele danych. Listę tworzymy za pomocą nawiasów kwadratowych

```python
dane = ["adres", "numer", "imię"]
```

Aby odczytać zawartość listy, należy podać adres elementu który chcemy odczytać w nawiasach kwadratowych, np. `dane[0]` odczytują pierwszy obiekt z listy, a `dane[2] = "nazwisko"` zmienia zawartość trzeciego obiektu.
Podanie liczby ujemnej jako adresu sprawi że zaczniemy odczytywać od końca, np. `dane[-1]` to element ostatni.

**Uwaga - elementy listy są numerowane od 0 (element na początku ma numer 0, kolejny ma numer 1 itd.)**

## Operacje na listach

### Dodawanie elementów

Aby dodać element na końcu listy używamy metody `append()`:

`dane.append("wzrost")`

### Usuwanie elementów

Aby usunąć element z listy znając jego miejsce, używamy polecenia `del`:

`del dane[2]`

Słowo kluczowe `del` może służyć też do usuwania całych obiektów albo funkcji:

```python
data = [1, 2, 3, 4, 5]
del data
len(data) # error!
```

### Statystyki listy

Długość listy, czyli ilość elementów która się na niej znajduje, możemy odczytać funkcją `len()`, a sumę wszystkich elementów policzy funkcja `sum()`. Dostępne są także funkcje `min()` i `max()` (najmniejszy i największy element).

```python
dane = [1,2,3,4,5]
len(dane) # 5
sum(dane) # 15
```

### Inne operacje

Inne metody jakie możemy wykonywać na liście to: `insert()`, `pop()`, `remove()`, `clear()`, `sort()`, `copy()`, `extend()`. Ich opis można znaleźć w dokumentacji. Istnieją też bardziej zaawansowane funkcje, tj. `enumerate()`, `zip()`, `filter()` i `map()`, ich opis można znaleźć w dodatku.

### Funkcje a metody

Aby posortować listę możemy użyć **metody** `sort()`. Po użyciu tej metody elementy w liście zostaną przeniesione na nowe miejsca. Jeżeli chcemy posortować listę tylko tymczasowo, możemy użyć **funkcji** `sorted()`, która tworzy kopię listy i ją sortuje. Użycie zmiennej `reverse=True` sprawia że sortowanie będzie w odwrotnej kolejności niż domyślna.
Aby odwrócić kolejność elementów na liście używa się tej samej techniki. **Metoda** `reverse()` odwraca utworzoną listę, a **funkcja** `reversed()` odwraca ją tymczasowo.

Metoda różni się od funkcji tym, że metody są zawsze zarejestrowane tylko dla obiektów danej klasy, np. metoda dla `reverse()` dla list, metoda `lower()` dla stringów itp., a wywołuje się je używając kropki. Funkcje są elementem niezależnym, i wywołuje się je bez kropki.

```python
lista2 = lista1.copy()
lista1.sort()
lista1.reverse()
lista1 == sorted(lista2, reverse=True) # True
lista1 == lista2 # False
```

## Listy liczbowe

Aby utworzyć listę zawierającą ciąg liczbowy, możemy skorzystać z funkcji `range()`. Może ona tworzyć ciąg kolejnych liczb `range(1,11)` (ciąg od 1 do 10) lub ciąg arytmetyczny `range(1,10,2)` (ciąg liczb nieparzystych od 1 do 9)
Aby wynik funkcji range zamienić na listę, należy użyć polecenia `list(range())`

## Iteracja przez listę

Aby wykonać jakąś operację na każdym elemencie listy, nieważne jaka jest jej długość, używamy pętli for.

```python
for liczba in range(1,11):
    print(liczba**2)
```

Nie deklarujemy wartości zmiennej `liczba`, jest to zmienna pomocnicza. Przyjmuje ona po kolei wartość wszystkich zmiennych z listy `lista_liczb`, i wykonuje polecenia zawarte w pętli for.

## Lista składana

Listy składane to sposób na uproszczenie zapisu poprzez stworzenie listy bezpośrednio w wyrażeniu for, i jednoczesnym wykorzystaniu zmiennej pomocniczej:

**Uwaga: instrukcja tworzenia listy składanej musi znajdować się w kwadratowych nawiasach**

```python
kwadraty = [i**2 for i in list(range(1,11))]
```

W wyrażeniu listy składanej można również umieścić wyrażenia warunkowe:

```python
numbers = [1, 2, 5, 8, 10, 13]
parzyste = [number for number in numbers if number % 2 == 0]
```

## Sprawdzenie listy

Aby sprawdzić czy dany element znajduje się na liście lub nie, użyjemy słowa kluczowego `in` w inny sposób. Może ono tworzyć wyrażenie logiczne w połączeniu z listą.

```python
5 in range(1, 10) # True
"cztery" in ["raz", "dwa", "trzy"] # False
```

## Kopiowanie listy

Aby skopiować listę nie wystarczy użyć przypisania `nowa_lista = stara_lista`, ponieważ w ten sposób nadal istnieje jedna lista, ale o dwóch nazwach. Aby skopiować listę należy skorzystać z metody `copy()`

## Krotki (_tuple_)

Krotka jest konstrukcją podobną do listy, ale jej elementy nie mogą być modyfikowane. Tworzy się ją za pomocą okrągłych nawiasów lub funkcji `tuple`. Główną funkcją krotki jest przechowywanie stałych i niezmiennych wartości.

```python
krotka = (2, 5, 7)
krotka2 = tuple((2, 5, 7))
print(krotka[0]) # 2
krotka[2] = 8 # niedozwolone
```

## Ćwiczenia:

1. Stwórz kilka list z dowolnymi danymi i spróbuj wypisać pierwszy, drugi, ostatni i przedostatni element.
2. Przetestuj działanie jednej z dodatkowych funkcji działających na listach, opisanych w dokumentacji.
3. Wygeneruj kilka ciągów liczbowych za pomocą funkcji `range()`.

## Zadania:

1. Stwórz program który będzie zawierał listę imion wszystkich uczestników warsztatów, a następnie usuń swoje imię i dodaj je na końcu.
2. Stwórz listę z dowolnymi liczbami i znajdź największą z nich bez używania funkcji `max()`.
3. Policz średnią wartość wszystkich liczb z zakresu od 1 do 1000000. [online](https://parsons.problemsolving.io/puzzle/5d6f43383c1943a6bd2639e2f4267254)
4. Stwórz program który zapyta użytkownika o dwie liczby, a następnie policzy sumę wszystkich liczb parzystych pomiędzy nimi. [online](https://parsons.problemsolving.io/puzzle/e8d62b4044a1477f8921d75b4537a037)
5. Za pomocą moduły `turtle` stwórz wielokolorową figurę która każdy bok będzie miała w innym kolorze. [dostępne kolory](https://htmlcolorcodes.com/color-names/)

### Trening generowania list

Aby poćwiczyć tworzenie list, rozwiąż następujące zadania. W miarę możliwości skorzystaj z list składanych.

1. znajdź wszystkie liczby od 1 do 1000 podzielne przez 7
2. wypisz pewną liczbę kolejnych potęg dwójki
3. z listy zawierającej różne typy danych odfiltruj tylko dane typu całkowitego (funkcja `type()`)
4. policz liczbę spacji w zdaniu
5. znajdź wszystkie wyrazy w danym zdaniu które mają mniej niż 4 litery (przydatna metoda `split()`)

### Rośliny

```python
[
    "Aloe Vera", "Snake Plant", "Spider Plant", "Peace Lily", "ZZ Plant", "Monstera Deliciosa", "Pothos", "Philodendron", "Rubber Plant", "Bird's Nest Fern",
    "Boston Fern", "Chinese Money Plant", "Jade Plant", "Fiddle Leaf Fig", "Areca Palm", "Dracaena", "Calathea", "Peperomia", "Dieffenbachia", "English Ivy",
    "Cast Iron Plant", "Swiss Cheese Plant", "Croton", "String of Pearls", "Elephant Ear", "Dumb Cane", "Oxalis", "Heartleaf Philodendron", "Golden Pothos", "Anthurium",
    "Prayer Plant", "Air Plant", "Hoya", "Kentia Palm", "Christmas Cactus", "Dwarf Banana Plant", "Rex Begonia", "Asparagus Fern", "Bromeliad", "Zebra Plant",
    "Umbrella Plant", "Arrowhead Plant", "African Violet", "Maranta", "Parlor Palm", "Rubber Tree", "Lady Palm", "Alocasia", "Chinese Evergreen", "Kalanchoe",
    "Silver Queen", "Lucky Bamboo", "Peace Lily", "Variegated Rubber Plant", "Bird of Paradise", "Moth Orchid", "Corn Plant", "Guzmania", "Lipstick Plant", "Golden Barrel Cactus",
    "Crown of Thorns", "Baby Rubber Plant", "Silver Satin Pothos", "Rattlesnake Plant", "Echeveria", "Pilea", "Spiderwort", "Ming Aralia", "Succulent Mix",
    "Fatsia Japonica", "Indian Fern", "Yucca", "Flamingo Lily", "Fishbone Cactus", "Desert Rose", "Split Leaf Philodendron", "Golden Cane Palm", "Blue Star Fern",
    "Coral Cactus", "White Bird of Paradise", "Senecio", "Money Tree", "Snake Plant Laurentii", "Chinese Fan Palm", "Velvet Leaf Philodendron", "Chain of Hearts", "Silver Nerve Plant",
    "Staghorn Fern", "Purple Passion Plant", "String of Bananas", "Kangaroo Paw Fern", "Wax Plant", "Grape Ivy", "Watermelon Peperomia", "Olive Plant",
    "Crassula Ovata", "Tiger Aloe", "Arrowhead Vine", "Moses in the Cradle", "Pink Anthurium", "Green Shamrock Plant", "Dwarf Umbrella Tree", "Sago Palm"
]
```

1. Skopiuj powyższą listę roślin, i zamień wszystkie nazwy na pisane małymi literami.
2. Policz rośliny których nazwa zaczyna się na 'a'.
3. Wypisz wszystkie rośliny których nazwa zaczyna się od samogłoski i wypisz je posortowane.
4. Wypisz roślinę która posiada najdłuższą nazwę ze wszystkich.
5. Pobierz od użytkownika nazwę rośliny i sprawdź czy znajduje się na liście.

## Test:

Czy poniższe programy prawidłowo usuną liczby parzyste z listy? Jeżeli nie, to co się stanie z listą?
Może przydać się do tego [Python tutor](https://pythontutor.com)

```python
data = [1, 2, 3, 4, 5, 6]

for i in data:
    if i%2 == 0:
        del i
```

```python
data = [1, 2, 3, 4, 5, 6]

data = [n for n in data if n%2 != 0]
```

```python
data = [1, 2, 2, 2, 3, 4, 5, 6]

x = 0
while x < len(data):
    if data[x]%2 == 0:
        del data[x]
    x += 1
```

## Projekt

Za pomoca list możemy stworzyć system podróżowania i zdobywania przedmiotów.

1. Stwórz listę miejsc które gracz może odwiedzić. Następnie dodaj możliwość by gracz wpisywał do której lokalizacji z mapy chce sie przenieść.

2. Przy wejściu do niektórych lokalizacji dodaj możliwość zdobycia przedmiotu, np. jeżeli gracz wejdzie do lasu, to otrzymuje napój leczący, jeżeli wejdzie do jaskini otrzymuje klucz itp.
   Przedmioty gracza powinny być przechowywane również na liście.

3. Wejście do zamku powinno być mozliwe tylko jeżeli gracz posiada klucz, i wtedy rozgrywa się walka z bossem.

4. Do każdej z lokalizacji możesz dodac też inne wydarzenia, minibossy, postaci dodatkowe itp.
