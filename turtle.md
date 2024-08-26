---
title: "Turtle"
permalink: /turtle
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

## Moduł Turtle
Aby usprawnić naukę programowania, możemy dodać do naszych programów elementy tworzenia grafiki, ruchu i animacji. Uproszczony interfejs graficzny przeznaczony do nauki programowania oferuje moduł Turtle - wzorowany na języku *logo* z lat 80.
Pozwala on na stworzenie okna graficznego z wirtualną ikoną "żółwia", a następnie poruszanie etym żółwiem. Poruszający się żółw pozostawia za sobą linię, co pozwala rysować kształty geometryczne.

Aby użyć modułu turtle musimy go zaimportować komendą `import`, a następnie każde polecenie powiązane z tą biblioteką musimy zaczynać od `turtle`.
Podstawowe komendy służące do poruszania się po ekranie to:
- `forward` lub `fd` / `backward` lub `bk` - porusza się naprzód lub do tyłu o określoną liczbę kroków
- `left` lub `lt` / `right` lub `rt` - obraca się w lewo lub w prawo o określony kąt

Program rysujący kąt prosty. Polecenie `turtle.done()` jest niezbędne aby program nie wyłączył się sam po zakończeniu rysowwania.

```python
import turtle

turtle.forward(100)
turtle.right(90)
turtle.forward(100)
turtle.done()
```


## Ćwiczenia:
1. Stwórz program który narysuje kwadrat
