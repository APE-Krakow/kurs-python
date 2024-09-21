---
title: "Turtle"
permalink: /turtle
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

<https://docs.python.org/3/library/turtle.html>

## Moduł Turtle
Aby usprawnić naukę programowania, możemy dodać do naszych programów elementy tworzenia grafiki, ruchu i animacji. Uproszczony interfejs graficzny przeznaczony do nauki programowania oferuje moduł Turtle - wzorowany na języku *logo* z lat 80.
Pozwala on na stworzenie okna graficznego z wirtualną ikoną "żółwia", a następnie poruszanie tym "żółwiem". Poruszający się żółw pozostawia za sobą linię, co pozwala rysować kształty geometryczne.

Aby użyć modułu turtle musimy go zaimportować komendą `import`, a następnie każde polecenie powiązane z tą biblioteką musimy zaczynać od `turtle`.
Podstawowe komendy służące do poruszania się po ekranie to:
- `forward`; `fd` / `backward`; `bk` - porusza się naprzód lub do tyłu o określoną liczbę kroków
- `left`; `lt` / `right`; `rt` - obraca się w lewo lub w prawo o określony kąt

Program rysujący kąt prosty. Polecenie `turtle.done()` jest niezbędne aby program nie wyłączył się sam po zakończeniu rysowania.

```python
import turtle

turtle.forward(100)
turtle.right(90)
turtle.forward(100)
turtle.done()
```

Mamy dodatkowo do dyspozycji narzędzia do manipulacji stylem rysowania:
- `penup`; `up` / `pendown`; `down` - podniesienie lub opuszczenie pióra (po podniesieniu pióra żółw porusza się, ale nie rysuje linii)
- `pencolor` - ustawia kolor pióra na podany. Aby ustawić kolor należy wpisać jego nazwę, np. `"red"`, `"yellow"`, `"blue"` itp. lub kod hex.

Ponadto możemy stworzyć wielokąty, posługując się metodą `begin_poly()` i `end_poly()`.

## Pętla
Pętla pozwala wykonać jedno polecenie wiele razy. Wykonuje ona polecenia tak długo, dopóki jest spełniony warunek podany w poleceniu.

```python
i = 0
while i < 3:
    turtle.forward(100)
    turtle.right(60)
    i += 1
```

Szczególnym przypadkiem jest nieskończona pętla `while`, tworzona z warunku który jest zawsze prawdziwy (np. `True`):

```python
while True:
    decyzja = input("Czy chcesz zakończyć program?/n")
    if decyzja == "Tak" or decyzja == "tak":
        break
```

## Ćwiczenia:
1. Stwórz program który narysuje kwadrat, zwyczajnie i przy użyciu pętli.
2. Stwórz program który narysuje inne kształty (np. sześciokąt, ośmiokąt itp.).
3. Stwórz program który pozwoli użytkownikowi wybrać jaki kształt ma zostać narysowany.
4. Stwórz przy pomocy modułu `Turtle` nieskończoną spiralę wychodzącą ze środka ekranu [online](https://parsons.problemsolving.io/puzzle/0bee1e5988cb419faf5b971df0098bc9)
5. Wspólnie stwórzmy rysunek za pomocą turtle [codeshare](https://codeshare.io).

