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
- `forward()`; `fd()` / `backward()`; `bk()` - porusza się naprzód lub do tyłu o określoną liczbę kroków
- `left()`; `lt()` / `right()`; `rt()` - obraca się w lewo lub w prawo o określony kąt w stopniach

Program rysujący kąt prosty. Polecenie `turtle.done()` jest niezbędne aby program nie wyłączył się sam po zakończeniu rysowania.

```python
import turtle

turtle.forward(100)
turtle.right(90)
turtle.forward(100)
turtle.done()
```

Mamy dodatkowo do dyspozycji narzędzia do manipulacji stylem rysowania:
- `penup()`; `up()` / `pendown()`; `down()` - podniesienie lub opuszczenie pióra (po podniesieniu pióra żółw porusza się, ale nie rysuje linii)
- `pencolor()` - ustawia kolor pióra na podany. Aby ustawić kolor należy wpisać jego nazwę, np. `"red"`, `"yellow"`, `"blue"` itp. lub kod hex.
- `speed()` - ustawia prędkość żółwia, dostępne wartości to `"fastest"`, `"fast"`, `"normal"`, `"slow"`, `"slowest"`. Tryb `"fastest"` oznacza że ruch jest natychmiastowy.

Ponadto możemy wypełnić kształt kolorem, posługując się metodą `begin_fill()` i `end_fill()`.

## Pętla
Pętla pozwala wykonać jedno polecenie wiele razy. Wykonuje ona polecenia tak długo, dopóki jest spełniony warunek podany w poleceniu.

```python
i = 0
while i < 3:
    turtle.forward(100)
    turtle.right(60)
    i += 1
```

Szczególnym przypadkiem jest nieskończona pętla `while`, tworzona z warunku który jest zawsze prawdziwy (np. `True`). Każdą pętlę możemy przerwać instrukcją `break`:

```python
while True:
    decyzja = input("Czy chcesz zakończyć program?/n")
    if decyzja == "Tak" or decyzja == "tak":
        break
```
## Test:
Co narysuja na ekranie poniższe programy, o ile nie zatrzymają się z powodu błędu? Czy pętla jest skonsrtuowana prawidłowo?

```python
import turtle

answer = int(input("Ile kółek narysować?\n"))
x = 0
while answer >= x:
    turtle.circle(20)
    turtle.fd(40)
    x = x - 1

turtle.done()
```

```python
import turtle

turtle.speed("fast")
while True:
    turtle.forward(400)
    turtle.left(175)
    if abs(turtle.pos()) < 1:
        break 

turtle.done()
```
## Ćwiczenia:
1. Stwórz program który narysuje kwadrat, zwyczajnie i przy użyciu pętli.
2. Stwórz program który narysuje inne kształty (np. sześciokąt, ośmiokąt itp.).
3. Stwórz program który pozwoli użytkownikowi wybrać jaki kształt ma zostać narysowany.
4. Stwórz przy pomocy modułu `turtle` nieskończoną spiralę wychodzącą ze środka ekranu [online](https://parsons.problemsolving.io/puzzle/0bee1e5988cb419faf5b971df0098bc9)
5. Narysuj gwiazdę wypełniona na niebiesko [online](https://parsons.problemsolving.io/puzzle/efa14f6e0c7f4bbca450b1ec2cb631b9)
6. Wspólnie stwórzmy rysunek za pomocą turtle [codeshare](https://codeshare.io)
7. Stwórz program który narysuje dany kształt kilkukrotnie, tworząc np. wzór z gwiazdek
