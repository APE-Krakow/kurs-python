---
layout: page
title: "Listy"
permalink: /listy
theme: jekyll-theme-tactile
---

# Listy (list)
## Tworzenie list
Za pomocą listy można stworzyć jedną zmienną przechowującą wiele danych. Listę tworzymy za pomocą nawiasów kwadratowych lub za pomocą polecenia `list`

```
dane = ["adres", "numer", "imię"]`
dane = list("adres", "numer", "imię")
```

Aby odczytać zawartość listy, należy podać pozycję na liście którą chcemy odczytać w nawiasach kwadratowych, np. `dane[0]` odczytują pierwszy obiekt z listy, a `dane[2] = "nazwisko"` zmienia zawartość trzeciego obiektu.
 
**Uwaga - elementy listy są numerowane od 0 (element na początku ma numer 0, kolejny ma numer 1 itd.)**
## Operacje na listach
Aby dodać element na końcu listy używamy metody `append()`:

`dane.append("wzrost")`

Aby usunąć element z końca listy, używamy metody `pop()`. Funkcja ta zwraca element który został usunięty:

`a = dane.pop()`

Możemy również sprecyzować który element chcemy "zdjąć" z listy:

`a = dane.pop(2)`

Aby usunąć element z listy znając jego miejsce, używamy polecenia `del`:

`del dane[2]`

Długość listy, czyli ilość elementów która się na niej znajduje, możemy odczytać funkcją `len()`, a sumę wszystkich elementów policzy funkcja `sum()`

```
dane = list(1,2,3,4,5)
len(dane) == 5
sum(dane) == 15
```

Aby usunąć z listy znany element używamy metody `remove()`:

`dane.remove("imię")`

Aby połączyć dwie listy możemy użyć operatora `+` lub metody `extend()`:

```
lista_c = lista_a + lista_b
lista_a.extend(lista_b)
lista_c == lista_a
```

Aby posortować listę na stałe, możemy użyć metody `sort()`. Metoda `sorted()` zwraca posortowaną listę, ale nie wprowadza do niej stałych zmian. Użycie zmiennej `reverse=True` sprawia że sortowanie będzie w odwrotnej kolejności niż domyślna. 
Podobnie działa kolei użycie metody `reverse()`, która odwraca utworzoną listę i metoda `reversed()`, która odwraca ją tymczasowo.

```
lista2 = lista1.copy()
lista1.sort()
lista1.reverse()
lista1 == lista2.sorted(reverse=True)
lista1 != lista2
```

## Listy liczbowe
Aby utworzyć listę zawierającą ciąg liczbowy, możemy skorzystać z funkcji `range()`. Może ona tworzyć ciąg kolejnych liczb `range(1,11)` (ciąg od 1 do 10) lub ciąg arytmetyczny `range(1,10,2)` (ciąg liczb nieparzystych od 1 do 9)
Aby wynik funkcji range zamienić na listę, należy użyć polecenia `list(range())`

## Iteracja przez listę
Aby wykonać jakąś operację na każdym elemencie listy, nieważne jaka jest jej długość, używamy pętli for.

```
lista_liczb = list(range(1,11))
for liczba in lista_liczb:
    print(liczba**2)
```
Nie deklarujemy wartości zmiennej `liczba`, jest to zmienna pomocnicza. Przyjmuje ona po kolei wartość wszystkich zmiennych z listy `lista_liczb`, i wykonuje polecenia zawarte w pętli for.

Drugim typem pętli jest pętla while. Wykonuje ona polecenia tak długo, dopóki jest spełniony warunek podany w poleceniu.

```
i = 0
lista_liczb = list(range(1,11))
while i < len(lista_liczb):
    print(lista_liczb[i]**2)
    i += 1
```

Jak widać, pętla while jest bardziej skomplikowana w działaniu, ale dzięki takiej konstrukcji wiemy zawsze który element listy podlega zmianie w danym momencie. Szczególnym przypadkiem jest nieskończona pętla while, tworzona z warunku który jest zawsze prawdziwy:
`while True:`

## Lista składana
Listy składane to sposób na uproszczenie zapisu poprzez stworzenie listy bezpośrednio w wyrażeniu for, i jednoczesnym wykorzystaniu zmiennej pomocniczej:

**Uwaga: instrukcja tworzenia listy składanej musi znajdować się w kwadratowych nawiasach**

``` 
kwadraty = [i**2 for i in list(range(1,11))]
```

## Wycinki listy
Można uzyskać dostęp do fragmentu listy, wskazując pierwszy element i element za ostatnim elementem wycinka:

``wycinek = lista[2:5]``

Polecenie to utworzy wycinek od trzeciego do piątego elementu listy (elementy o numerach 2-4, ale musimy pamiętać że pierwszy element ma numer 0)

Można pozostawić jeden koniec wycinka otwarty:

``wycinek = lista [2:]``

W ten sposób powstał wycinek od trzeciego elementu do końca.

## Kopiowanie listy
Aby skopiować listę nie wystarczy użyć przypisania `nowa_lista = stara_lista`, ponieważ w ten sposób nadal istnieje jedna lista, ale o dwóch nazwach. Aby skopiować listę należy utworzyć wycinek od początku do końca listy `nowa_lista = stara_lista[:]`, lub skorzystać z metody `copy()`

## Krotki (tuple)
Krotka jest konstrukcją podobną do listy, ale jej elementy nie mogą być modyfikowane. Tworzy się ją za pomocą okrągłych nawiasów lub funkcji `tuple`. Główną funkcją krotki jest przechowywanie stałych i niezmiennych wartości.

```
krotka = (2, 5, 7)
krotka2 = tuple(2, 5, 7)
krotka[0] == 2  #True
krotka[2] = 8 #niedozwolone
```
## Zadania:
1. Stwórz listę która będzie przechowywać nazwy trzech marek samochodów. Następnie dodaj do niej dwa samochody, jeden na końcu a drugi na początku listy.
2. Stwórz program który dla każdego pojazdu znajdującego się na liście wypisze komunikat informujący że znajduje się on w kolekcji.
3. Stwórz kopię listy samochodów, posortuj ją i policz marki samochodów zaczynające się na 'a'.
4. Stwórz program który zapyta użytkownika o dwie liczby, a następnie policzy sumę wszystkich liczb parzystych pomiędzy nimi.
