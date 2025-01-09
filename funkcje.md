---
title: "Funkcje"
permalink: /funkcje
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

Często jeden fragment programu trzeba wykorzystać więcej niż jeden raz. Aby za każdym razem nie musieć pisać tych samych poleceń, możemy stworzyć funkcję i wywoływać ją za każdym razem kiedy chcemy skorzystać z jej działania. Funkcja jest nazwanym podprogramem który można uruchomić wielokrotnie. Funkcje tworzy się za pomocą słowa kluczowego `def` (definition), a po nazwie funkcji muszą wystąpić okrągłe nawiasy:

```python
def greet():
    name = input("podaj swoje imię ")
    print(f"witaj {name}")

greet()
greet()
```

Aby stworzyć pustą funkcję (np. do wypełnienia później), zamiast jej treści należy wpisać słowo kluczowe `pass`, które nic nie robi.

## Argumenty funkcji

Funkcje mogą przyjmować od użytkownika dane (argumenty), które wykorzystają w swoim działaniu. Argumenty te należy umieścić w okrągłym nawiasie:

```python
def greet(name, birthday):
    if not birthday:
        print(f"witaj {name}")
    else:
        print(f"wszystkiego najlepszego {name}")

greet("Maciek", True)
greet("Ania", False)
```

## Argumenty domyślne

Niektóre argumenty mogą posiadać wartości domyślne, które zostaną przyjęte jeżeli użytkownik nie poda żadnej wartości danego argumentu.
**Argumenty domyślne powinny znajdować się na samym końcu listy argumentów**

Możliwe jest również wywołanie funkcji poprzez nazwanie wszystkich argumentów, nie muszą one wtedy być w odpowiedniej kolejności.

```python
def greet(name, birthday=False):
    if not birthday:
        print(f"witaj {name}")
    else:
        print(f"wszystkiego najlepszego {name}")

greet(birthday=True, name="Maciek")
greet("Ania")
```

## Zwracanie wartości

Podobnie jak funkcje matematyczne zawsze dają wynik, np. `f(x) = 4x + 2` dla argumentu `x = 5` zwraca wartość `22` podobnie funkcje w programowaniu funkcje zawsze zwracają jakąś wartość, która może być dowolnego typu.
Jeżeli jej nie sprecyzujemy, to będzie ona `None`.
Możliwe jest sprecyzowanie jaka to ma być wartość za pomocą słowa kluczowego `return`.
Na przykład funkcja z początku tego akapitu w Pythonie brzmiałaby:

```python
def fun(x):
    return 4 * x + 2
```

Inny przykład funkcji w Pythonie:

```python
def mean(data):
    return sum(data) / len(data)

grades = [2, 5, 6, 3, 2, 4]
print(mean(grades))
```

## Zwracanie więcej niż jednej wartości

Funkcja może zwrócić wyłącznie jeden obiekt po zakończeniu działania. Aby ominąć to ograniczenie, funkcja może zwrócić krotkę zawierającą więcej niż jedną wartość. Aby odczytać te wartości można użyć funkcjonalności zwanej _rozpakowywaniem krotki_:

```python
time = (15, 30)
hour, minute = time
print(hour) #15
print(minute) #30
```

```python
def read_time():
    return (15, 30)

hour, minute = read_time()
```

## Rekurencja i iteracja

Aby funkcja mogła wykonać wiele operacji, można zastosować podejście rekurencyjne albo iteracyjne. Iteracja polega na stworzeniu wewnątrz funkcji pętli `for` lub `while`, wykonującej polecenia taką ilość razy jaka jest potrzebna. Podejście rekurencyjne polega na wywoływaniu funkcji przez samą siebie, w celu znalezienia ostatecznego wyniku. Najważniejsze w funkcji iteracyjnej jest zamieszczenie warunku stopu - warunku który pozwoli przestać wywoływać funkcję w nieskończoność.

Poniżej zamieszczono przykład rekurencyjnego o i iteracyjnego obliczania silni z danej liczby. W wypadku funkcji rekurencyjnej najważniejszy jest warunek `0` i `1`.
Dla tych wartości silnia jest znana z definicji i one oznaczają zakończenie wywoływania funkcji.

Funkcje rekurencyjne często mogą działać wolniej, jednak są prostsze w projektowaniu w przypadku zaawansowanych algorytmów i struktur danych typu np. drzewo, graf itp.

```python
def factorial(x):
    if x == 0 or x == 1:
        return 1
    else:
        return x * factorial(x-1)
```

```python
def factorial(x):
    sum = 1
    for i in range(1, x+1):
        sum *= i
    return sum
```

## Importowanie

### Import modułu

Nie wszystkie funkcje są dostępne jako standardowe funkcje Pythona. Brakuje chociażby tak przydatnej funkcji jak pierwiastkowanie. Aby uzyskać dostęp do zewnętrznych bibliotek należy użyć słowa kluczowego `import`. Pozwala to na użycie funkcji które są zapisane w innych plikach. Większość z często używanych funkcji została już stworzona i znajduje się w **Bibliotece Standardowej** Pythona. Na przykład funkcja pierwiastkowania `sqrt()` znajduje się w module matematycznym `math`. Aby jej użyć, należy zaimportować moduł matematyczny, i wywoływać go przy uruchomieniu funkcji.

```python
import math
math.sqrt(16)
```

### Import poszczególnych funkcji

Polecenie `from math import sqrt` pozwoli nam używać tej funkcji bez przedrostka `math`. Aby zaimportować więcej funkcji można wymienić je po przecinku, np. `from math import sqrt, factorial, abs`. Przy importowaniu można nadać funkcji nową nazwę (alias) za pomocą słowa kluczowego `as`. Na przykład `from X import Y as Z`. Od tej pory funkcja Y jest dostępna, ale wyłącznie pod nazwą Z.

```python
import numpy as np
from math import sqrt
from mymath import sqrt as mysqrt

np.sqrt(16) # funkcja sqrt z numpy
sqrt(16) # funkcja sqrt z math
mysqrt(16) # funkcja sqrt z mymath
```

### Import własnych modułów

Każdy plik stworzony przez użytkownika jest traktowany jako osobny moduł, więc można je importować tak samo jak moduły Pythona, o ile znajdują się w tym samym katalogu. Na przykład aby zaimportować funkcję `show()` z pliku `graphics.py` należy skorzystać z `from graphics import show`.

## Typy zmiennych

Aby przekazać innym użytkownikom programu jakiego typu argumenty powinni przekazać do funkcji, można wskazać sugerowany typ w definicji funkcji. Nie ma to żadnego wpływu na działanie programu, jest jedynie sugestią dla innych programistów jak z niej korzystać. Można też wskazać jaki typ jest zwracany przez daną funkcję.

```python
def how_many_grater_than(data: list, value: int) -> int:
    return len([i for i in data if i > value])
```

## Ćwiczenia:

1. Stwórz funkcję która wykona dowolne równanie matematyczne i wypisze jego wynik.
2. Dodaj możliwość aby to użytkownik wprowadził liczby do działania matematycznego poprzez argumenty.
3. Jeżeli użytkownik nie poda liczby, niech zostanie użyta jakaś wartość domyślna.
4. Zamiast wypisywać wynik na ekranie, niech funkcja zwraca wartość działania jako liczbę.
5. Dodaj do funkcji kilka bardziej skomplikowanych działań matematycznych z biblioteki `math`.

## Zadania:

1. Napisz funkcję która przyjmuje krotkę będącą przedziałem liczbowym oraz inną liczbę, i sprawdza czy liczba ta mieści się w przedziale. [online](https://parsons.problemsolving.io/puzzle/9f8dae21faa4421da15e7d8ce1420ce0)

2. Napisz funkcję które będzie przyjmować listę liczb, usuwać z niej wszystkie zduplikowane wartości i zwraca wyczyszczoną listę.
   [online](https://parsons.problemsolving.io/puzzle/2e0f6d990f0c4e919833c1221dd59b6d)

3. Napisz funkcję która przyjmuje kilka danych na temat użytkownika, i zwraca słownik zawierający te dane. W wypadku jeżeli użytkownik nie poda jakiejś informacji, pole powinno być wypełnione przez "brak danych". [online](https://parsons.problemsolving.io/puzzle/6173528edabc46f38f898d8fe59762fa)

4. Napisz funkcje które będą mogły obsługiwać szyfr Cezara (szyfr polegający na tym że kolejne liczby w wiadomości są przesunięte do przodu lub do tyłu o daną liczbę).
   Jedna funkcja powinna umożliwiać zaszyfrowanie teksu (powinna przyjmować tekst oraz liczbę o jaką trzeba przesunąć zawartość), a druga funkcja powinna odszyfrowywać (powinna przyjmować zaszyfrowany tekst oraz liczbę o jaką trzeba wrócić).
   Aby sprawdzić czy funkcje działają, trzeba sprawdzić czy po zaszyfrowaniu i odszyfrowaniu tekst jest taki sam.
   Do zamieniania znaków na liczby przyda się funkcja `ord()` oraz działająca odwrotnie funkcja `chr()`.

5. Napisz funkcję rekurencyjną i iteracyjną wypisującą kolejne elementy ciągu Fibonacciego. Ciąg ten składa się z liczb, z których każda jest sumą dwóch poprzednich, a dwiema pierwszymi liczbami ciągu są jedynki.
   1, 1, 2, 3, 5, 8, 13, 21, ...

6. Napisz grę w zgadywanie. Program powinien wylosować jakąś liczbę, a następnie poprosić użytkownika o podanie wartości. Potem powinien informować użytkownika czy liczba którą podał jest za duża, czy za mała, tak długo aż użytkownik nie trafi na właściwą liczbę. Aby wylosować liczbę z jakiegoś przedziału, należy użyć funkcji `randrange(start, end+1)` z biblioteki `random`. `start` i `end` to krawędzie przedziału z którego ma być wylosowana liczba.

7. Stwórz program odwrotny do gry w zgadywanie. Niech tym razem to program zgaduje jaką liczbę wymyślił sobie użytkownik. Postaraj się aby program mógł odczytywać wiele możliwych odpowiedzi użytkownika, np. "Większa", "Więcej", "za dużo" itp. za pomocą osobnej funkcji.

8. Stwórz program rysujący na zawołanie w `turtle`. Dodaj do niego funkcje rysujące wybrane kształty, np. wielokąt, gwiazdę, owal itp.
   Pozwól aby użytkownik wybierał gdzie kształty będą się znajdować na ekranie.
   Możesz komunikować się z użytkownikiem za pomocą funkcji `turtle.textinput()` albo `turtle.numinput()` które pozwalają tworzyć wyskakujące okienka pytające o daną liczbę.
   Program można stworzyć wspólnie korzystając z [codeshare](https://codeshare.io).

````

## Projekt

Dzięki funkcjom możemy rozdzielić często używane elementy programu i wykorzystywać je jako funkcje.

1. Rozdziel do osobnych funkcji części związane z wyświetlaniem mapy, powitania, zakończenia, walki itp. Dzięki temu pozostanie nam jedynie główna pętla, w której będą znajdować się wywołania funkcji.

2. Dodaj system menu, który w każdej lokacji pozwala wybrać różne aktywności.

3. Przenieś kod funkcji związanych z graczem do osobnego pliku, np. `player.py` a z lokacjami do `locations.py`, i importuj tylko te które sa potrzebne.

## Test

Czy poniższe programy zadziałają, a jeżeli nie to z jakiego powodu, i co można w nich poprawić?

```python
def calculate(a, b, c, d = 5, e = 8):
    return (a+b) / (c*d + e)

calculate(2, 3, 4, c=4, e=2)
````

```python
def arithmetic_sum(x):
    return x + arithmetic_sum(x-1)

print(arithmetic_sum(50))
```

`assert` to słowo kluczowe używane do wykrywania błędów, jeżeli wartość logiczna przy `assert` ma wartość `False`, program kończy się z błędem.

```python
x = 5

def set_x(new_x):
    x = new_x

def get_x():
    return x

assert get_x() == 5
set_x(20)
assert x == 20
```
