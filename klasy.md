---
title: "Klasy"
permalink: /klasy
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

Często istnieje potrzeba przechowywania danych o bardziej skomplikowanej strukturze niż na to pozwalają domyślnie wbudowane typy. W tym celu można stworzyć własne typy danych (nazywane klasami) i ich obiekty. Klasę tworzy się za pomocą słowa kluczowego `class` oraz stworzenie pól klasy przechowujących dane.

```python
class Wspolrzedne:
    x = 0
    y = 0
    z = 0
```

Klasa jest jednak tylko wzorcem na podstawie którego można tworzyć obiekty. Dopiero po stworzeniu obiektu danej klasy można odczytać wartość jego pól. Na podstawie jednej klasy można stworzyć dowolną ilość obiektów, z których każdy może przyjąć inne wartości pól.

```python
nowe_wspolrzedne = Wspolrzedne()
nowe_wspolrzedne.x = 5
print(nowe_wspolrzedne.x)
```

## Metody
Metody to funkcje które są wbudowane w klasę i mogą być wywoływane na jej obiektach. Wywołana metoda ma dostęp do pól klasy za pomocą obiektu `self`. Obiekt ten jest odwołaniem do obiektu na którym jest wywołana metoda. Obiekt `self` musi być zawsze pierwszym argumentem metody klasy.

```python
class Wspolrzedne:
    x = 0
    y = 0
    z = 0

    def ustaw_wspolrzedne(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z

nowe_wspolrzedne = Wspolrzedne()
nowe_wspolrzedne.ustaw_wspolrzedne(1,2,3)
print(nowe_wspolrzedne.x)
```

## Konstruktor
Aby mieć wpływ na tworzenie obiektu, możemy edytować specjalną funkcję `__init__()`, która jest wywoływana przy tworzeniu każdego obiekty klasy. Ta funkcja nazywana jest konstruktorem. Jeżeli jakieś pole klasy zostaje zainicjowane w konstruktorze, to nie ma już później potrzeby deklarować go osobno.

```python
class Wspolrzedne:
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z

    def suma(self):
        return self.x + self.y + self.z

nowe_wspolrzedne = Wspolrzedne(1,2,3)
print(nowe_wspolrzedne.suma())
```

## Dodatkowe funkcje obiektów
Każdy obiekt może być usunięty za pomocą słowa kluczowego `del`

```python
start = Wspolrzedne(0, 0, 0)
koniec = Wspolrzedne(23, 78, 56)
del koniec
```

## Ćwiczenia:
1. Stwórz klasę przechowującą dane o jakiejś roślinie. Może zawierać takie informacje jak gatunek, wiek, ile dni temu była podlana, itp.
2. Dodaj do klasy `Roslina` metodę obliczającą, czy należy ją ponownie podlać.
3. Dodaj metodę `podlej`, która wyzeruje ilość dni od ostatniego podlania.
3. Zmień tworzenie obiektu `Roslina` na metodę `__init__()`.
4. Dodaj funkcję globalną `zraszacz()`, która przyjmie całą listę roślin i podleje każdą z nich.

## Zadania:
### Szkoła
1. Utwórz klasy reprezentującą nauczycieli i uczniów. Mogą one zawierać takie dane jak imię, nazwisko, wiek. Dodatkowo nauczyciel może posiadać listę przedmiotów których może uczyć, a uczeń klasę do której chodzi i listę swoich ocen. Dodaj metodę do obliczenia średniej ocen ucznia.

2. Stwórz klasę reprezentującą klasę szkolną. Może ona zawierać listę uczniów i wychowawcę oraz słownik zawierający poszczególne dni i frekwencję klasy na dany dzień. Dodaj metody pozwalające np. wypisać listę uczniów i średnią ocen klasy. Dodaj też metodę pozwalającą nauczycielowi sprawdzić obecność i zapisać frekwencję klasy.

3. Stwórz klasę reprezentującą szkołę. Szkołą powinna składać się z listy klas. Dodaj możliwość sprawdzenia średniej ocen dla całej szkoły oraz frekwencję w całej szkole dla danego dnia, oraz dla całego kalendarza.

### Sklep
[shop.py](https://github.com/APE-Krakow/tasks/blob/main/shop.py)
1. Stwórz klasę która będzie reprezentować przedmiot w sklepie (posiada nazwę, cenę, dostępną ilość). Wartości powinny być inicjalizowane w konstruktorze. Stwórz kilka obiektów tej klasy. Następnie stwórz funkcję, która poda wartość dla podanej ilości produktów.

2. Zmień działanie poprzedniej klasy, tak żeby podanie wartości produktów danego typu odbywało się z poziomu obiektu (poprzez metodę wbudowaną)

3. Stwórz klasę reprezentującą sklep, która będzie zawierała zbiór przedmiotów dostępnych do zakupu. Poprzez metody powinna być możliwość sprawdzenia stanu magazynu (najlepiej w formie tabeli), oraz zakupu jakiegoś przedmiotu. Uwaga - funkcja powinna być odporna na kogoś kto chciałby kupić więcej przedmiotów niż jest w magazynie, kupić ujemną ilość przedmiotów itp.
