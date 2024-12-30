---
title: "Podstawy"
permalink: /podstawy
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

## Tryby działania

### Tryb interaktywny

Aby zapoznać się z działaniem Pythona, możemy uruchomić tryb interaktywny, w którym Python będzie wykonywał każde polecenie natychmiast po tym jak je wpiszemy. Python nie posiada własnej grafiki, dlatego przesyła się do niego tekst używając terminala:

- powershell, cmd (Windows)
- terminal (Linux/Mac)

W tryb interaktywny wchodzimy poprzez wpisanie polecenia `python`. Będąc w trybie interaktywnym widzimy znak zachęty `>>>`. Aby z niego wyjść używamy funkcji `exit()`
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

Linux: `python /home/user/plik.py`

## Typy danych

Dane wprowadzane do programu są przechowywane w pamięci w różny sposób, w zależności od tego jakiego rodzaju wartość reprezentują. Wyróżniamy następujące podstawowe typy (oczywiście jest ich dużo więcej, oraz użytkownik może tworzyć swoje własne, ale te są najprostsze w rozpoznaniu)

- liczba całkowita `int`
- liczba rzeczywista (zmiennoprzecinkowa) `float`
- dane tekstowe `str`
- zmienna logiczna (`True`/`False` **wartości logiczne zaczynają się z wielkiej litery**) `bool`

Aby dowiedzieć się jakiego typu jest zmienna `x`, używamy funkcji `type(x)`

## Operacje na tekście

Aby połączyć dwie zmienne tekstowe możemy użyć zwykłego znaku +. Nie zadziała to jednak gdy jedna ze zmiennych nie jest tekstem, a na przykład liczbą. W takim wypadku musimy użyć funkcji konwersji, o nazwie takiej samej jak typ na który konwertujemy. Na przykład żeby skonwertować zmienną liczbową `a` na zmienną tekstową, należy użyć funkcji `str(a)`.

```python
a = "numer"
b = 3
print(a + str(b))
```

Istnieje również lepszy sposób łączenia zmiennych z programu z tekstem: _format string_. Działa on jak tworzenie zwykłego napisu, ale jeżeli przez cudzysłowem dodamy znak `f`, możemy wewnątrz tekstu umieszczać zmienne programu wewnątrz nawiasów klamrowych '{}'.

```python
a = "numer"
b = 3
print(f"Twój {a} to {b}")
# Twój numer to 3
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

Stwierdzeniem logicznym jest takie wyrażenie, które może być skonwertowane do typu logicznego `bool` (`True` albo `False`). Podstawowym typem testu warunkowego jest porównanie wartości zmiennych. W tym celu używa się następujących operatorów:

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

### Łączenie warunków

Aby sprawdzić jednocześnie kilka warunków, możemy je połączyć za pomocą operatorów logicznych **i** oraz **lub** (`and`/`or`).

## Test

Co wypiszą na ekranie poniższe programy, o ile nie zatrzymają się z powodu błędu?

```python
from datetime import datetime

name = input("Podaj imię\n")
condition = "True"

if condition:
    print(f"Dzień dobry {name}, jest {datetime.now()}")
```

```python
x = input("podaj pierwszą liczbę\n")
y = input("podaj drugą liczbę\n")
operation = input("Podaj działanie\n")

if operation == '+':
    print(int(x+y))
elif operation == '-':
    print(int(x-y))
```

## Zadania

1. Stwórz program który będzie realizował dowolne działanie matematyczne: zapyta użytkownika o dwie liczby, wykona działanie i wypisze wynik.

2. Stwórz program który pozwala zrealizować jedno z dwóch działań: dodawanie lub odejmowanie [online](https://parsons.problemsolving.io/puzzle/a46fd0aa513042d08e623eedbfb8e1c1)

3. Stwórz program który pobierze od użytkownika dane osobowe, a następnie wypisze dla tego użytkownika powitanie. Pamiętaj aby forma powitania zgadzała się z zaimkami jakie ta osoba poda!

4. Stwórz program przeprowadzający test kompetencji. Część pytań powinna akceptować odpowiedź tekstową a część w formie liczb. Za prawidłową odpowiedź użytkownik powinien dostawać punkt, a na koniec powinien otrzymać pochwałę jeżeli otrzymał pewną ilość punktów.
   Program można stworzyć wspólnie korzystając z [codeshare](https://codeshare.io).

5. Napisz program, który oceni czy dany rok (podany przez użytkownika) jest rokiem przestępnym czy nie. Rok jest przestępny, jeżeli jest podzielny przez 4 i nie jest podzielny przez 100, lub jeżeli jest podzielny przez 400.

## Projekt

Po każdym module kursu korzystając ze świeżo zdobytej wiedzy, możemy tworzyć części większego projektu, np. gry RPG. Na koniec kursu będziemy posiadać gotową grę.

Pierwszym elementem gry może być system uruchamiania i symulacja walki z bossem zadającym zagadki.

1. Stwórz ekran tytułowy gry np. za pomocą ASCII art. Poczekaj aż użytkownik naciśnie jakiś przycisk, a następnie wyczyść ekran (można to zrobić za pomocą `print(\033c)`)
2. Poproś użytkownika o podanie nazwy użytkownika itp., a następnie znów wyczyść ekran.
3. Wyświetl informację o rozpoczęciu wyprawy lub przygody.
4. Zasymuluj walkę z przeciwnikiem, który zadaje graczowi zagadki.
5. Jeżeli użytkownik odpowiedział poprawnie, wyświetl komunikat o wygraniu gry.
