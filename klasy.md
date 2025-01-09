---
title: "Klasy"
permalink: /klasy
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

Często istnieje potrzeba przechowywania danych o bardziej skomplikowanej strukturze niż na to pozwalają domyślnie wbudowane typy danych, takie jak `int` czy `str`. W tym celu można stworzyć własne typy danych (nazywane klasami) i ich obiekty. Klasę tworzy się za pomocą słowa kluczowego `class` oraz stworzenie pól klasy przechowujących dane.

```python
class Coordinates:
    x = 0
    y = 0
    z = 0
```

Klasa jest jednak tylko wzorcem na podstawie którego można tworzyć obiekty, tak samo jak `int` nie ma zdefiniowanej wartości. Dopiero po stworzeniu obiektu danej klasy można odczytać wartość jego pól. Na podstawie jednej klasy można stworzyć dowolną ilość obiektów, z których każdy może przyjąć inne wartości pól.

```python
my_coordinates = Coordinates()
my_coordinates.x = 5
new_coordinates = Coordinates()
new_coordinates.x = 10
```

## Metody

Metody to funkcje które są wbudowane w klasę i mogą być wywoływane na jej obiektach. Wywołana metoda ma dostęp do pól klasy za pomocą obiektu `self`. Obiekt ten jest odwołaniem do obiektu na którym jest wywołana metoda. Obiekt `self` musi być zawsze pierwszym argumentem metody klasy.

```python
class Coordinates:
    x = 0
    y = 0
    z = 0

    def set_coordinates(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z

my_coordinates = Coordinates()
my_coordinates.set_coordinates(1, 2, 3)
print(my_coordinates.x)
```

## Konstruktor

Aby mieć wpływ na tworzenie obiektu, możemy edytować specjalną funkcję `__init__()`, która jest wywoływana przy tworzeniu każdego obiekty klasy. Ta funkcja nazywana jest konstruktorem. Jeżeli jakieś pole klasy zostaje zainicjowane w konstruktorze, to nie ma już później potrzeby deklarować go osobno.

```python
class Coordinates:
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z

    def sum(self):
        return self.x + self.y + self.z

my_coordinates = Coordinates(1,2,3)
print(my_coordinates.sum())
```

## Dodatkowe funkcje obiektów

Każdy obiekt może być usunięty za pomocą słowa kluczowego `del`

```python
start = Coordinates(0, 0, 0)
end = Coordinates(23, 78, 56)
del end
```

## Ćwiczenia:

[online](https://parsons.problemsolving.io/puzzle/75acbab3ba1a449e81c8cac4381a71e5)

1. Stwórz klasę `Plant` przechowującą dane o jakiejś roślinie. Może zawierać takie informacje jak gatunek, wiek, ile dni temu była podlana, ile razy łącznie była podlana itp.
2. Dodaj metodę `water`, która wyzeruje ilość dni od ostatniego podlania i zwiększy licznik podlań.
3. Dodaj do klasy `Plant` metodę `needs_water` obliczającą, czy należy ją ponownie podlać.
4. Zmień tworzenie obiektu `Plant` na metodę `__init__()`.
5. Dodaj funkcję globalną `sprinkler()`, która przyjmie całą listę roślin i podleje każdą która tego wymaga.

## Zadania:

### Książka kucharska

1. Przygotuj system cyfrowej książki kucharskiej. Różne przepisy mogą być reprezentowane w klasie `Recipe`. Klasa ta może posiadać listę składników, listę ocen danej potrawy, nazwę itp.
2. Dodaj metodę która pozwala dodać nową ocenę oraz metodę która wyświetla średnią ocen danej potrawy.
3. Stwórz funkcję która porówna dwie potrawy i wypisze jakie składniki występują w obu przepisach.

### Sklep

[shop.py](https://github.com/APE-Krakow/tasks/blob/main/shop.py)

1. Stwórz klasę która będzie reprezentować przedmiot w sklepie (posiada nazwę, cenę, dostępną ilość). Wartości powinny być inicjalizowane w konstruktorze. Stwórz kilka obiektów tej klasy. Następnie stwórz funkcję, która poda wartość dla podanej ilości produktów.

2. Zmień działanie poprzedniej klasy, tak żeby podanie wartości produktów danego typu odbywało się z poziomu obiektu (poprzez metodę wbudowaną)

3. Stwórz klasę reprezentującą sklep, która będzie zawierała zbiór przedmiotów dostępnych do zakupu. Poprzez metody powinna być możliwość sprawdzenia stanu magazynu (najlepiej w formie tabeli), oraz zakupu jakiegoś przedmiotu. Uwaga - funkcja powinna być odporna na kogoś kto chciałby kupić więcej przedmiotów niż jest w magazynie, kupić ujemną ilość przedmiotów itp.

## Projekt

Dodaj interfejsy obiektowe do często używanych komponentów aby uprościć korzystanie z nich.

1. Zmień wszystkie funkcje związane z graczem na klasę `Player` z atrybutami takimi jak imię, klasa, hp, zebrane przedmioty itp.

2. Zmień funkcje związane z lokacjami na klasę `Location`. Lokacje moga zawierać w sobie listy przedmiotów, wrogów, itp.

3. Dodaj nową klasę `Enemy`, która będzie posiadała swoją własną nazwę, hp, nagrodę za pokonanie itp. Rozmieść kilku wrogów w różnych lokacjach i dodaj funkcję która będzie odpowiadała za przeprowadzenie walki.

## Test

Czy poniższe programy zadziałają, a jeżeli nie to z jakiego powodu, i co można w nich poprawić?

```python
class Liquid:
    def __init__(self, volume, density):
        mass = volume * density

water = Liquid(5, 1000)
print(water.mass)
```

```python
class Greeter:
    def greet():
        return "Hello"
    def supergreet():
        return "Hello hello hello!"

print(Greeter.supergreet)
```
