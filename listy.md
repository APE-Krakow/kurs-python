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

Aby dodać element w dowolnym miejscu listy, używamy metody `insert()`, dodając miejsce na liście na które chcemy dodać dane:

`dane.insert(2, "numer telefonu")`

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

## Dostęp do numeru iteracji
Czasem musimy wiedzieć, na którym aktualnie elemencie listy się znajdujemy. W takim wypadku pomoże nam funkcja `enumerate()`, która dodaje do kolejnych elementów listy numery z oznaczeniem ich miejsca

```python
for n, i in enumerate([4, 7, 2, 8, 9, 0]):
    print(f"element {n} listy to {i}")
```

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

## Kopiowanie listy
Aby skopiować listę nie wystarczy użyć przypisania `nowa_lista = stara_lista`, ponieważ w ten sposób nadal istnieje jedna lista, ale o dwóch nazwach. Aby skopiować listę należy skorzystać z metody `copy()`

## Krotki (*tuple*)
Krotka jest konstrukcją podobną do listy, ale jej elementy nie mogą być modyfikowane. Tworzy się ją za pomocą okrągłych nawiasów lub funkcji `tuple`. Główną funkcją krotki jest przechowywanie stałych i niezmiennych wartości.

```python
krotka = (2, 5, 7)
krotka2 = tuple((2, 5, 7))
print(krotka[0]) # 2
krotka[2] = 8 # niedozwolone
```

## Ćwiczenia:
1. Stwórz kilka list z dowolnymi danymi i spróbuj wypisać pierwszy, drugi, ostatni i przedostatni element.
2. Wygeneruj kilka ciągów liczbowych za pomocą funkcji `range`.

## Zadania:
1. Stwórz progam który będzie zawierał listę imion wszystkich uczestników warsztatów, a następnie usuń swoje imię i dodaj je na końcu.
2. Stwórz listę z dowolnymi liczbami i znajdź największą z nich bez używania funkcji `max()`.
3. Wypisz wszystkie liczby z zakresu od 1 do 1000000, a następnie policz ich średnią wartość. [online](https://parsons.problemsolving.io/puzzle/3cee48da763d4a3ea5e10934812f3eb0)
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
1. Stwórz listę która będzie przechowywać nazwy trzech roślin. Następnie dodaj do niej dwie nowe rośliny, jedną na końcu a drugą na początku listy.
2. Stwórz program który dla każdej rośliny znajdującej się na liście wypisze komunikat informujący że znajduje się ona w kolekcji.
3. Stwórz kopię listy roślin, posortuj ją i policz rośliny których nazwa zaczyna się od litery "a".
4. Stwórz program który będzie wypisywał wszystkie rośliny których nazwa zaczyna się od samogłoski.
5. Usuń z listy co drugi element, zaczynając od pierwszego.
6. Policz która litera występuje najczęściej wśród wszystkich liter w nazwach na liście. 

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
