---
title: "Listy (list)"
permalink: /listy
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

## Tworzenie list
Za pomocą listy można stworzyć jedną zmienną przechowującą wiele danych. Listę tworzymy za pomocą nawiasów kwadratowych lub za pomocą funkcji `list()`

```python
dane = ["adres", "numer", "imię"]
dane = list( ("adres", "numer", "imię") )
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
Aby usunąć element z końca listy, używamy metody `pop()`. Funkcja ta zwraca element który został usunięty:

`a = dane.pop()`

Możemy również sprecyzować który element chcemy "zdjąć" z listy:

`a = dane.pop(2)`

Aby usunąć element z listy znając jego miejsce, używamy polecenia `del`:

`del dane[2]`

Aby usunąć z listy znany element używamy metody `remove()`:

`dane.remove("imię")`

### Statystyki listy
Długość listy, czyli ilość elementów która się na niej znajduje, możemy odczytać funkcją `len()`, a sumę wszystkich elementów policzy funkcja `sum()`

```python
dane = list(1,2,3,4,5)
len(dane) # 5
sum(dane) # 15
```

### Łączenie list
Aby połączyć dwie listy możemy użyć operatora `+` lub metody `extend()`:

```python
lista_c = lista_a + lista_b
lista_a.extend(lista_b)
lista_c == lista_a
```

### Inne operacje
Aby posortować listę możemy użyć metody `sort()`. Po użyciu tej metody elementy w liście zostaną przeniesione na nowe miejsca. Jeżeli chcemy posortować listę tylko tymczasowo, możemy użyć funkcji `sorted()`, która tworzy kopię listy i ją sortuje. Użycie zmiennej `reverse=True` sprawia że sortowanie będzie w odwrotnej kolejności niż domyślna.
Aby odwrócić kolejność elementów na liście używa się tej samej techniki. Metoda `reverse()` odwraca utworzoną listę, a funkcja `reversed()` odwraca ją tymczasowo.

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
lista_liczb = list(range(1,11))
for liczba in lista_liczb:
    print(liczba**2)
```
Nie deklarujemy wartości zmiennej `liczba`, jest to zmienna pomocnicza. Przyjmuje ona po kolei wartość wszystkich zmiennych z listy `lista_liczb`, i wykonuje polecenia zawarte w pętli for.

Drugim typem pętli jest pętla while. Wykonuje ona polecenia tak długo, dopóki jest spełniony warunek podany w poleceniu.

```python
i = 0
lista_liczb = list(range(1,11))
while i < len(lista_liczb):
    print(lista_liczb[i]**2)
    i += 1
```

Jak widać, pętla while jest bardziej skomplikowana w działaniu, ale dzięki takiej konstrukcji wiemy zawsze który element listy podlega zmianie w danym momencie. Szczególnym przypadkiem jest nieskończona pętla while, tworzona z warunku który jest zawsze prawdziwy:

```python
while True:
    decyzja = input("Czy chcesz zakończyć program?/n")
    if decyzja == "Tak" or decyzja == "tak":
        break
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

## Wycinki listy
Można uzyskać dostęp do fragmentu listy, wskazując pierwszy element i element za ostatnim elementem wycinka:

```python
wycinek = lista[2:5]
```

Polecenie to utworzy wycinek od trzeciego do piątego elementu listy (elementy o numerach 2-4, ale musimy pamiętać że pierwszy element ma numer 0)

Można pozostawić jeden koniec wycinka otwarty:

```python
wycinek = lista [2:]
```

W ten sposób powstał wycinek od trzeciego elementu do końca.

## Kopiowanie listy
Aby skopiować listę nie wystarczy użyć przypisania `nowa_lista = stara_lista`, ponieważ w ten sposób nadal istnieje jedna lista, ale o dwóch nazwach. Aby skopiować listę należy utworzyć wycinek od początku do końca listy `nowa_lista = stara_lista[:]`, lub skorzystać z metody `copy()`

## Krotki (*tuple*)
Krotka jest konstrukcją podobną do listy, ale jej elementy nie mogą być modyfikowane. Tworzy się ją za pomocą okrągłych nawiasów lub funkcji `tuple`. Główną funkcją krotki jest przechowywanie stałych i niezmiennych wartości.

```python
krotka = (2, 5, 7)
krotka2 = tuple((2, 5, 7))
print(krotka[0]) #2
krotka[2] = 8 #niedozwolone
```

## Ćwiczenia:
1. Stwórz kilka list z dowolnymi danymi i spróbuj wypisać pierwszy, drugi, ostatni i przedostatni element.

## Zadania:
1. Stwórz listę która będzie przechowywać nazwy trzech roślin. Następnie dodaj do niej dwie nowe rośliny, jedną na końcu a drugą na początku listy.
2. Stwórz program który dla każdej rośliny znajdującej się na liście wypisze komunikat informujący że znajduje się ona w kolekcji.
3. Stwórz kopię listy roślin, posortuj ją i policz rośliny których nazwa zaczyna się od litery "a".
4. Stwórz program który będzie wypisywał wszystkie rośliny których nazwa zaczyna się od samogłoski.
5. Usuń z listy co drugi element, zaczynając od pierwszego.
6. Policz która litera występuje najczęściej wśród wszystkich liter w nazwach na liście. 
7. Stwórz program który zapyta użytkownika o dwie liczby, a następnie policzy sumę wszystkich liczb parzystych pomiędzy nimi. [online](https://parsons.problemsolving.io/puzzle/e8d62b4044a1477f8921d75b4537a037)
8. Aby poćwiczyć tworzenie list składanych rozwiąż z pomocą tej metody następujące zadania:
    1. znajdź wszystkie liczby od 1 do 1000 podzielne przez 7
    2. wypisz pewną liczbę kolejnych potęg dwójki
    3. z listy zawierającej różne typy danych odfiltruj tylko dane typu całkowitego
    5. policz liczbę spacji w zdaniu
    6. znajdź wszystkie wyrazy w danym zdaniu które mają mniej niż 4 litery
