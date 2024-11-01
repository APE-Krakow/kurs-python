---
title: "Dodatkowe informacje"
permalink: /dodatek
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

## Główna biblioteka Pythona
<https://docs.python.org/3/library/index.html>

## Konwencje nazw
Aby już po samej nazwie obiektu można było się zorientować co zawiera, przyjęły się określone zasady nazywania obiektów w programie. Co do zasady wszystkie dokumenty związane z programowaniem powinny być w języku angielskim 

### Zmienne:
* nazwa powinna zawierać małe litery i podkreślniki, np. `address_data`
* długość nazwy zmiennej powinna być wprost proporcjonalna do czasu jej trwania, tj. zmienna globalna wykorzystywana wielokrotnie powinna nazywać się `main_database_server_address`, a zmienna wewnętrzna użyta kilka razy może nazywać się `server`
* nazwy jednoliterowe powinny być używane tylko jako liczniki, np. `i, j, k` albo `n`
* zmienne typu `bool` najlepiej aby miały nazwę w formie przymiotnika, np. `is_palindrome`, `emergency_communication_available`

### Funkcje:
* nazwy funkcji powinny spełniać te same wymagania co nazwy zmiennych
* najlepiej aby nazwy funkcji były czasownikami opisującymi co dana funkcja wykonuje, np. `sort_users_by_name()`, `display_interface()`
* argumenty funkcji są zmiennymi lokalnymi więc ich nazwy powinny być krótkie

### Klasy:
* nazwy klas powinny być zapisane używając CamelCase, np. `WindowManager`, `MainDatabaseConnection`
* jeżeli jakaś klasa jest tylko interfejsem po którym pozostałe klasy mają dziedziczyć, na początku jego nazwy można dodać "I", np. `IGamePlayer`
* podobnie jak we wszystkich pozostałych obiektach, im bardziej powszechnie używana jest klasa, jej nazwa powinna być bardziej szczegółowa

## Formatowanie tekstu
Formatować tekst można za pomocą funkcji `format()` albo za pomocą tzw. *format stringów* (stringów typu `f""`). Obie metody są równoznaczne i stanowią po prostu różne formy zapisu tego samego.

```python
"{} to ładny kolor, {} też".format(color1, color2)
f"{color1} to ładny kolor, {color2} też"
```

Dodatkowo *format string* pozwala na nazwanie kolejnych pól

```python
"Nazywam się {imie}. {imie} {nazwisko}".format(imie="James", nazwisko="Bond")
```

Aby w konkretny sposób dostosować zapis poszczególnych pól, możemy użyć specjalnych znaczników:
### Wyrównanie:
* `<` wyrównane do lewej, wartość domyślna dla typów tekstowych.
* `>` wyrównane do prawej, wartość domyślna dla typów liczbowych.
* `=` wyrównane do prawej, z wyjątkiem znaku, który jest wyrównany do lewej.
* `^` wyśrodkowanie
### Znak:
* `+` Umieszcza `+` przed liczbami dodatnimi i `-` przed liczbami ujemnymi
* `-` Nie umieszcza niczego przed liczbami dodatnimi i `-` przed liczbami ujemnymi (domyślne)
* Pusta spacja umieszcza spację wiodącą przed liczbami dodatnimi i `-` przed liczbami ujemnymi.
### Precyzja:
`X.Y` służy do wyrównania długości pola. `X` oznacza długość całej zmiennej, a `Y` przedstawia ile cyfr po przecinku ma być wyświetlonych.
### Typ:
w zależności od typu zmiennej używane są specjalne sposoby do sformatowania tekstu. Dostępne typy to:

| litera | znaczenie        |
|--------|------------------|
|d       |liczba dziesiętna |
|b       |format binarny    |
|o       |format ósemkowy   |
|x lub X |format szestnastkowy|
|e lub E |notacja naukowa   |
|f lub F |liczba zmiennoprzecinkowa|
|g lub G |zwykły format     |
|c       |pojedynczy znak   |
|r       |String (repr())   |
|s       |String (str())    |
|%       |wartość procentowa|

### Przykłady:
* liczba dziesiętna `x` wyśrodkowana na polu o szerokości 10 znaków: `{x:^10d}`
* liczba zmiennoprzecinkowa `x`, z dwoma miejscami po przecinku i znakiem: `{x:+.2}`

## Dodatkowe sposoby zapisu
Aby rozbić jednolinijkowy tekst na kilka linijek w kodzie, można połączyć je nawiasami:

```python
tekst = ("jedna "
         "długa "
         "linijka "
         "tekstu")
```

Aby rozbić wielolinijkowy tekst na kilka linijek w kodzie, można użyć potrójnego cudzysłowu:

```python
tekst = """Tekst posiadający
        wiele linijek
        może być bardzo długi"""
```

## Przeciążanie metod
Wiele funkcji w pythonie zachowuje się inaczej, jeżeli zostanie wywołana dla różnych obiektów. Na przykład funkcja `print()` działa inaczej dla ciągów znakowych, a inaczej dla list. Dzieje się tak dlatego, że każdy obiekt ma w sobie zakodowaną metodę definiującą w jaki sposób zamienić go na tekst nadający się do wyświetlenia na ekranie. Posiadają go także obiekty definiowane przez użytkownika. (Jeżeli nie zostaną zdefiniowane ręcznie, to interpreter stworzy je automatycznie). Znając nazwy tych metod można zdefiniować w jaki sposób nasz obiekt zachowa się przy wywołaniu funkcji.

Konwersja:

- `__str__(self)` - wywoływana przy konwersji na `string`, np. przy wywołaniu funkcji `print()`
- `__int__(self)` - wywoływana przy konwersji na `int`
- `__float__(self)` - wywoływana przy konwersji na `float`
- `__repr__(self)` - wywołane przy konwersji na tekst przy użyciu `repr()`

Operacje matematyczne:

- `__add__(self, other)` - dodawanie
- `__sub__(self, other)` - odejmowanie
- `__mul__(self, other)` - mnożenie
- `__floordiv__(self, other)` - dzielenie całkowite (operator `//`)
- `__truediv__(self, other)` - dzielenie zmiennoprzecinkowe (operator `/`)
- `__mod__(self, other)` - modulo (operator %)
- `__pow__(self, other)` potęga (operator `**`)

Konstruktor i destruktor:

- `__init__(self)` - wywoływany przy tworzeniu obiektu
- `__del__(self)` - wywoływany przy usuwaniu obiektu z pamięci, albo za pomocą polecenia `del`, albo w momencie gdy zakończy się czas życia obiektu

Operacje porównania:

- `__eq__(self, other)` wynik porównania *equal* `==`
- `__ne__(self, other)` wynik porównania *not equal* `!=`
- `__lt__(self, other)` wynik porównania *less than* `<`
- `__gt__(self, other)` wynik porównania *greater than* `>`
- `__le__(self, other)` wynik porównania *less or equal* `<=`
- `__ge__(self, other)` wynik porównania *greater or equal* `>=`

## Wycinki listy
Można uzyskać dostęp do fragmentu listy, wskazując pierwszy element i element za ostatnim elementem wycinka:

```python
wycinek = lista[2:5]
```

Polecenie to utworzy wycinek od trzeciego do piątego elementu listy (elementy o numerach 2-4, ale musimy pamiętać że pierwszy element ma numer 0)

Można pozostawić jeden koniec wycinka otwarty:

```python
wycinek = lista [2:]
```

W ten sposób powstał wycinek od trzeciego elementu do końca.

## Specjalne funkcje dla list
Istnieje kilka zaawansowanych metod które można używać w połączeniu z listami aby uprościć działanie programu

`enumerate()`, `zip()`, `filter()` i `map()`
