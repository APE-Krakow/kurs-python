---
layout: page
title: "Dodatek"
permalink: /dodatek
---

# Dodatkowe informacje:
## Konwencje nazw
Aby już po samej nazwie obiektu można było się zorientować co zawiera, przyjęły się określone zasady nazywania obiektów w programie. Co do zasady wszystkie dokumenty związane z programowaniem powinny być w języku angielskim 

### Zmienne:
* nazwa powinna zawierać małe litery i podkreślniki, np. `address_data`
* długość nazwy zmiennej powinna być wprost proporcjonalna do czasu jej trwania, tj. zmienna globalna wykorzystywana wielokrotnie powinna nazywać się `main_database_server_address`, a zmienna wewnętrzna użyta kilka razy może nazywać się `server`
* nazwy jednoliterowe powinny być używane tylko jako liczniki, np. `i, j, k` albo `n`
* zmienne typu `bool` najlepiej aby miały nazwę w formie przymiotnika, np. `is_palindrome`, `communication_available`

### Funkcje:
* nazwy funkcji powinny spełniać te same wymagania co nazwy zmiennych
* najlepiej aby nazwy funkcji były czasownikami opisującymi co dana funkcja wykonuje, np. `sort_users_by_name()`, `display_interface()`
* argumenty funkcji są zmiennymi lokalnymi więc ich nazwy powinny być krótkie

### Klasy:
* nazwy klas powinny być zapisane używając CamelCase, np. `WindowManager`

## Przekazywanie zmiennych

## Formatowanie tekstu
### Dodatkowe sposoby zapisu
Aby rozbić jednolinijkowy tekst na kilka linijek można połączyć je nawiasami:

```
tekst = ("jedna "
         "długa "
         "linijka "
         "tekstu")
```

Aby rozbić wielolinijkowy tekst na kilka linii, można użyć potrójnego cudzysłowu:

```
tekst = """Tekst posiadający
        wiele linijek
        może być bardzo długi"""
```

## Dokumentacja

## Przeciążanie metod
Wiele funkcji w pythonie zachowuje się inaczej, jeżeli zostanie wywołana dla różmych obiektów. Na przykład funkcja `print()` działa inaczej dla ciągów znakowych, a inaczej dla list. Dzieje się tak dlatego, że każdy obiekt ma w sobie zakodowaną metodę definiującą w jaki sposób zamienić go na tekst nadający się do wyświetlenia na ekranie. Posiadają go także obiekty definiowane przez użytkownika. (Jeżeli nie zostaną zdefiniowane ręcznie, to interpreter stworzy je automatycznie). Znając nazwy tych metod można zdefiniować w jaki sposób nasz obiekt zachowa się przy wywołaniu funkcji.

Konwersja:

- `__str__(self)` - wywoływana przy konwersji na `string`, np. przy wywołaniu funkcji `print()`
- `__int__(self)` - wywoływana przy konwersji na `int`
- `__float__(self)` - wywoływana przy konwersji na float

Operacje matematyczne:

- `__add__(self, other)` - dodawanie
- `__sub__(self, other)` - odejmowanie
- `__mul__(self, other)` - mnożenie
- `__floordiv__(self, other)` - dzielenie całkowite (operator `//`)
- `__truediv__(self, other)` - dzielenie zmienniprzecinkowe (operator `/`)
- `__mod__(self, other)` - modulo (operator %)
- `__pow__` potęga (operator `**`)

Konstruktor i destruktor:

- __init__(self) - wywoływany przy tworzeniu obiektu
- `__del__(self)` - wywoływany przy usuwaniu obiektu z pamięci, albo za pomocą polecenia `del`, albo w momencie gdy zakończy się czas życia obiektu

Operacje porównania:

- `__eq__(self, other)` wynik porównania *equal* `==`
- `__ne__(self, other)` wynik porównania *not equal* `!=`
- `__lt__(self, other)` wynik porównania *less than* `<`
- `__gt__(self, other)` wynik porównania *greater than* `>`
- `__le__(self, other)` wynik porównania *less or equal* `<=`
- `__ge__(self, other)` wynik porównania *greater or equal* `>=`
