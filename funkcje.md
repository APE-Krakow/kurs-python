---
title: "Funkcje"
permalink: /funkcje
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

Często jeden fragment programu trzeba wykorzystać więcej niż jeden raz. Aby za każdym razem nie musieć pisać tych samych poleceń, możemy stworzyć funkcję i wywoływać ją za każdym razem kiedy chcemy skorzystać z jej działania. Funkcje tworzy się za pomocą słowa kluczowego `def`, a po nazwie funkcji muszą wystąpić okrągłe nawiasy:

```python
def powitanie():
    imie = input("podaj swoje imię")
    print(f"witaj {imie}")

powitanie()
powitanie()
```

Aby stworzyć pustą funkcję (np. do wypełnienia później), zamiast jej ciała należy wpisać słowo kluczowe `pass`

## Argumenty funkcji
Funkcje mogą przyjmować od użytkownika dane, które wykorzystają w swoim działaniu. Argumenty te należy umieścić w okrągłym nawiasie:

```python
def powitanie(imie, urodziny):
    if not urodziny:
        print(f"witaj {imie}")
    else:
        print(f"wszystkiego najlepszego {imie}")

powitanie("Maciek", True)
powitanie("Ania", False)
```

## Argumenty domyślne
Niektóre argumenty mogą posiadać wartości domyślne, które zostaną przyjęte jeżeli użytkownik nie poda żadnej wartości danego argumentu.
**Argumenty domyślne powinny znajdować się na samym końcu listy argumentów**

Możliwe jest również wywołanie funkcji poprzez nazwanie wszystkich argumentów.

```python
def powitanie(imie, urodziny=False):
    if not urodziny:
        print(f"witaj {imie}")
    else:
        print(f"wszystkiego najlepszego {imie}")

powitanie(urodziny=True, imie="Maciek")
powitanie("Ania")
```

## Zwracanie wartości
Po zakończeniu działania funkcji możliwe jest przekazanie informacji zwrotnej na temat jej działania za pomocą słowa kluczowego `return`.

```python
def srednia(lista):
    return lista.sum() / len(lista)

oceny = [2, 5, 6, 3, 2, 4]
print(srednia(oceny))
```

## Zwracanie więcej niż jednej wartości
Funkcja może zwrócić wyłącznie jeden obiekt po zakończeniu działania. Aby ominąć to ograniczenie, funkcja może zwrócić krotkę zawierającą więcej niż jedną wartość. Aby odczytać te wartości można użyć funkcjonalności zwanej *rozpakowywaniem krotki*:

```python
czas = (15, 30)
(godzina, minuta) = czas
print(godzina) #15
print(minuta) #30
```


```python
def podaj godzine():
    return (15, 30)

(godzina, minuta) = podaj_godzine()
```

## Rekurencja i iteracja
Aby funkcja mogła wykonać wiele operacji, można zastosować podejście rekurencyjne albo iteracyjne. Iteracja polega na stworzeniu wewnątrz funkcji pętli `for` lub `while`, wykonującej polecenia taką ilość razy jaka jest potrzebna. Podejście rekurencyjne polega na wywoływaniu funkcji przez samą siebie, w celu znalezienia ostatecznego wyniku.

```python
def silnia(x):
    if x==0:
        return 1
    elif x==1:
        return 1
    else:
        return x * silnia(x-1)
```

## Importowanie
### Import modułu
Nie wszystkie funkcje są dostępne jako standardowe funkcje Pythona. Brakuje chociażby tak przydatnej funkcji jak pierwiastkowanie. Aby uzyskać dostęp do zewnętrznych bibliotek należy użyć słowa kluczowego `import`. Pozwala to na użycie funkcji które są zapisane w innych plikach. Większość z często używanych funkcji została już stworzona i znajduje się w Bibliotece Standardowej Pythona. Na przykład funkcja pierwiastkowania `sqrt()` znajduje się w module matematycznym `math`. Aby jej użyć, należy zaimportować moduł matematyczny, i wywoływać go przy uruchomieniu funkcji.

```python
import math
math.sqrt()
```

### Import poszczególnych funkcji
Polecenie `from math import sqrt` pozwoli nam używać tej funkcji bez przedrostka `math`. Aby zaimportować więcej funkcji można wymienić je po przecinku, np. `from math import sqrt, factorial, abs`.Przy importowaniu można nadać funkcji nową nazwę (alias) za pomocą słowa kluczowego `as`. Na przykład `from X import Y as Z`. Od tej pory funkcja Y jest dostępna, ale wyłącznie pod nazwą Z.

### Import własnych modułów
Każdy plik stworzony przez użytkownika jest  traktowany jako osobny moduł, więc można je importować tak samo jak moduły Pythona, o ile znajdują się w tym samym katalogu.

## Zadania:
1. Napisz funkcję która przyjmuje krotkę będącą przedziałem liczbowym oraz liczbę, i sprawdza czy liczba ta mieści się w przedziale.

2. Napisz funkcję które będzie przyjmować listę liczb, usuwać z niej wszystkie zduplikowane wartości i zwraca wyczyszczoną listę.

3. Napisz funkcje które będą mogły obsługiwać szyfr Cezara dla liczb na liście (szyfr polegający na tym że kolejne liczby w wiadomości są przesunięte do przodu lub do tyłu o daną liczbę). Jedna funkcja powinna umożliwiać zaszyfrowanie listy (powinna przyjmować listę oraz liczbę o jaką trzeba przesunąć zawartość), a druga funkcja powinna odszyfrowywać (powinna przyjmować zaszyfrowaną listę oraz liczbę o jaką trzeba wrócić).
Aby sprawdzić czy funkcje działają, trzeba sprawdzić czy po zaszyfrowaniu i odszyfrowaniu ciąg liczb jest taki sam.

4. Napisz funkcję rekurencyjną i iteracyjną wypisującą kolejne elementy ciągu Fibonacciego. Ciąg ten składa się z liczb, z których każda jest sumą dwóch poprzednich, a dwiema pierwszymi liczbami ciągu są jedynki.
1, 1, 2, 3, 5, 8, 13, 21, ...

5. Napisz grę w zgadywanie. Program powinien wylosować jakąś liczbę, a następnie prosić użytkownika o podanie wartości. Potem powinien informować użytkownika czy liczba którą podał jest za duża, czy za mała, tak długo aż użytkownik nie trafi na właściwą liczbę. Aby wylosować jakąś liczbę, należy użyć funkcji `randrange(początek, koniec+1)` z biblioteki `random`.
