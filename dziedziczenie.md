---
title: "Dziedziczenie"
permalink: /dziedziczenie
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

Klasy mogą tworzyć wielowarstwową hierarchę przedstawiającą ich relacje do przedstawianych obiektów.
Na przykład klasy reprezentujące obiekty w grze mogą wyglądać następująco:

ObiektGraficzny:<br/>
├─FiguraGeometryczna:<br/>
│ ├─Prostokąt:<br/>
│ │ └─Kwadrat<br/>
│ ├─Koło<br/>
│ └─Trójkąt<br/>
└─Obrazek

W powyższym schemacie obiekt klasy Prostokąt jest jednocześnie obiektem klasy FiguraGeometryczna, który jest obiektem klasy ObiektGraficzny. Dzięki temu metody pozwalające na przykład na wyświetlanie obiektu na ekranie mogą być skoncentrowane w kodzie klasy ObiektGraficzny. Z drugiej strony dzięki takiemu podejściu, wszystkie figury geometryczne jakie stworzymy będą mogły być traktowane jako obiekty klasy FiguraGeometryczna, mimo że ich wewnętrzna struktura jest inna. Mechanizm który na to pozwala nazywa się dziedziczeniem.

```python
class FiguraGeometryczna:
    def __init__():
        self.obwod = 0
        self.pole = 0

class Kwadrat(FiguraGeometryczna):
    def ustaw_wartosci(a):
        self.obwod = 4*a
        self.pole = a**2
```

O ile nie zmieniamy konstruktora klasy pochodnej, konstruktor klasy rodzica jest wywoływany automatycznie i nie ma potrzeby tworzyć tych pól na nowo.

## Konstruktor klasy rodzica

Dostęp do pól i metod klasy rodzica możemy uzyskać w klasie potomnej za pomocą metody `super()`. W ten sposób możemy uruchomić nadpisane metody w klasie rodzica.

```python
class FiguraGeometryczna:
    def __init__(obwod, pole):
        self.obwod = obwod
        self.pole = pole

class Prostokat(FiguraGeometryczna):
     def __init__(a, b)
        self.a = a
        self.b = b
        super().__init__(2*a + 2*b, a*b)
```

## Ćwiczenia:

1. Stwórz klasę reprezentującą miejscowość, oraz dziedziczące po niej klasy wieś i miasto. Miejscowość powinna zawierać informacje wspólne, takie jak nazwa, liczba mieszkańców i powierzchnia, a klasy potomne mogą zawierać dodatkowe dane takie jak imię sołtysa/burmistrza, czy gminę/powiat.
2. Spraw aby klasy wsi i miasta w swoim konstruktorze wywoływały też konstruktor miejscowości.

## Zadania:

### Zoo

1. Stwórz bazową klasę zwierzę, która będzie posiadać pola takie jak kolor, liczbę nóg itp.
   Dodaj do klasy metodę info, która wypisze podstawowe informacje o zwierzęciu.
2. Stwórz klasy pies i gołąb, bazujące na klasie zwierzę. Do metody info dodaj informacje na temat tego gatunku. Dodaj także metodę głos, która zwróci dźwięk jaki wydaje to zwierzę.
3. Dodaj klasy owczarek niemiecki i golden retriever, które będą posiadały także informacje na temat rasy zwierzęcia.

### Wielokąty

1. Stwórz klasę czworobok, zawierającą obwód i listę boków. Obwód powinien być obliczany w konstruktorze na podstawie długości boków.
2. Stwórz klasę prostokąt, posiadającą dodatkowo pole. Konstruktor powinien korzystać z symetrii prostokąta.
3. Stwórz klasę kwadrat, upraszczającą jeszcze bardziej klasę prostokąt.

### Galeria

1. Stwórz klasę do obsługi cyfrowej galerii sztuki. Powinna ona zawierać listę na którą będą wpisywani użytkownicy, oraz słownik do którego będą wpisywane dzieła sztuki (emotikony) oraz tytuły. Do klasy dodaj metodę pozwalającą na wypisanie wszystkich użytkowników wraz z ich poziomem uprawnień.
2. Stwórz hierarchię klas reprezentującą użytkowników systemu do wystawiania dzieł sztuki. Podstawowy użytkownik powinien posiadać uprawnienia do wyświetlania obrazów po podaniu ich tytułu. Użytkownik artysta powinien mieć również możliwość dodawania obrazów. Użytkownik kurator powinien mieć możliwość tworzenia wystaw z utworzonych obrazów (wystawa to stworzenie podzbioru słownika z dziełami sztuki i wyświetlenie go).

## Projekt

Za pomoca dziedziczenia możemy dodać wyspecjalizowane klasy obiektów gry.

1. Stwórz kilka rodzajów wrogów korzystając z klasy `Enemy`, na przykład `Boss`, `Minibos`, `Goblin` itp. Każdy z nich może posiadać inny sposób walki, inną nagrodę itp.
2. Stwórz kilka rodzajów lokacji, np. `EnemyLocation` która zawiera wroga, `PuzzleLocation` która zawiera zagadkę do rozwiązania itp.
