---
title: "Podstawy"
permalink: /podstawy
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

## Instalacja pythona:
Windows: przez instalator pobrany ze [strony](https://www.python.org/downloads/) (należy zaznaczyć checkbox 'add to system path')

Ubuntu Linux: polecenie sudo apt install python3 python-as-python3
Arch Linux: sudo pacman -S python3

## Tryby działania
### Tryb interaktywny
W tryb interaktywny wchodzimy poprzez polecenie `python`(Windows)/`python3`(Linux). Aby z niego wyjść używamy funkcji `exit()`
W tym trybie działają wszystkie polecenia, takie jak:

- utworzenie nowej zmiennej `a=5`
- wypisanie istniejącej zmiennej `print(a)`
- dodawanie `a + b`
- odejmowanie `a - b`
- mnożenie `a * b`
- dzielenie całkowite (z zaokrągleniem w dół) `a // b`
- dzielenie zmiennoprzecinkowe `a / b`
- modulo (reszta z dzielenia) `a % b`
- potęgowanie `a ** b`

### Tryb skryptowy
Aby przyspieszyć działanie pythona, można spisać wszystkie polecenia do pliku z rozszerzeniem `.py` a następnie wywołać pythona z katalogu w którym znajduje się plik poleceniem `python plik.py`. Można również podać bezpośrednią ścieżkę do pliku.
Windows: `python C:\Users\username\plik.py`

Linux: `python3 /home/user/plik.py`

## Typy danych
Dane wprowadzane do programu są przechowywane w pamięci w różny sposób, w zależności od tego jakiego rodzaju wartość reprezentują. Wyróżniamy następujące podstawowe typy (oczywiście jest ich dużo więcej, oraz użytkownik może tworzyć swoje własne, ale te są najprostsze w rozpoznaniu)

- liczba całkowita `int`
- liczba rzeczywista (zmiennoprzecinkowa) `float`
- dane tekstowe `str`
- zmienna logiczna (`True`/`False` **wartości logiczne zaczynają się z wielkiej litery**) `bool`
- liczba zespolona `complex`

Aby dowiedzieć się jakiego typu jest zmienna `x`, używamy funkcji `type(x)`

## Operacje na tekście
Aby połączyć dwie zmienne tekstowe możemy użyć zwykłego znaku +. Nie zadziała to jednak gdy jedna ze zmiennych nie jest tekstem, a na przykład liczbą. W takim wypadku musimy użyć funkcji konwersji, o nazwie takiej samej jak typ na który konwertujemy. Na przykład żeby skonwertować zmienną liczbową `a` na zmienną tekstową, należy użyć funkcji `str(a)`.

```python
a = "numer"
b = 3
print(a + str(b))
```

Istnieje również wiele innych sposobów na które można łączyć dane i tekst (więcej o formatowaniu tekstu w dodatku na końcu):

```python
a = 5
b = "hello"
print("Write ", b, " " , str(a))
print("Write " + b + str(a))
print("Write {} {}".format(b, str(a)))
print(f"Write {b} {str(a)}")
```

## Odczytywanie danych od użytkowników
Funkcja `input` służy do przechwytywania danych wpisanych przez użytkownika terminalu.

```python
a = input("Podaj datę urodzenia")
```

Dane te zawsze mają jednak format tekstowy, aby odczytać liczbę należy dokonać konwersji:

```python
liczba = int(input("Podaj liczbę"))
```

## Podejmowanie decyzji w programie
### Testy warunkowe
Stwierdzeniem logicznym jest takie wyrażenie, które może być skonwertowane do typu logicznego bool (`True` albo `False`). Podstawowym typem testu warunkowego jest porównanie wartości zmiennych. W tym celu używa się następujących operatorów:

- sprawdzenie równości `==`
- sprawdzenie nierówności `!=`
- większe `>`
- mniejsze `<`
- większe bądź równe `>=`
- mniejsze bądź równe `<=`

**ważne aby przy sprawdzaniu równości użyć podwójnego znaku `==`, w przeciwnym razie przypiszemy tylko jedną zmienną do drugiej, co zostanie odczytane jako `True`**

### Instrukcje warunkowe
Kolejne instrukcje wykonywane przez program można uzależnić od wyniku testu warunkowego za pomocą konstrukcji `if ... :`

```python
if a > b:
    print("a jest większe")
```
Do tej konstrukcji można dodać blok `else`, aby wykonać instrukcję jeżeli ostatni test zwrócił fałsz

```python
if a > b:
    print("a jest większe")
else:
    print("a nie jest większe")
```
Aby sprawdzić kilka warunków, można korzystać z bloku `elif` (od słów else + if)

```python
if a > b:
    print("a jest większe")
elif b > a:
    print("b jest większe")
else:
    print("a i b są równe")
```
## Zadania:
1. Stwórz program który będzie realizował dowolne działanie matematyczne: zapyta użytkownika o dwie liczby, wykona działanie i wypisze wynik.

2. Stwórz program który pobierze od użytkownika dane osobowe, a następnie wypisze dla tego użytkownika powitanie. Pamiętaj aby forma powitania zgadzała się z zaimkami jakie ta osoba poda!

3. Stwórz program przeprowadzający test kompetencji. Część pytań powinna akceptować odpowiedź tekstową a część w formie liczb. Za prawidłową odpowiedź użytkownik powinien dostawać punkt, a na koniec powinien otrzymać pochwałę jeżeli otrzymał pewną ilość punktów.

