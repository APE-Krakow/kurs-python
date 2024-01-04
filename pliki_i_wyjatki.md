---
title: "PLiki i Wyjątki"
permalink: /pliki
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

## Pliki
### Otwieranie pliku
Aby móc zapisywać dane do pliku, plik należy najpierw otworzyć za pomocą funkcji `open(nazwa_pliki, tryb_dostępu)`. Tryb dostępu określa w jaki sposób będzie zachowywał się plik:

- r (read only) - plik tylko do odczytu. Jest to domyślny tryb dostępu
- r+ (read and write) - plik do odczytu i zapisu
- w (write only) - plik tylko do zapisu. Jeżeli plik wcześniej nie istniał to zostanie utworzony.
- w+ (write and read) - plik do zapisu i odczytu. 
- a (append only) - plik do dopisu. Nowe dane będą umieszczone na końcu pliku. Jeżeli plik wcześniej nie istniał to zostanie utworzony.
- a+ (append and read) - plik do dopisu i odczytu. Nowe dane będą umieszczone na końcu pliku. Jeżeli plik wcześniej nie istniał to zostanie utworzony.

Dodatkowo plik można otworzyć jako:
* t - plik tekstowy (domyślnie) - tekst czytelny dla człowieka
* b - plik binarny - dane w formie zer i jedynek czytelne tylko dla innych programów


Należy pamiętać aby po zakończeniu obsługi pliku zamknąć go metodą `close()`.

```python
file = open("database.txt", "rt")
file.close()
```

### Odczytywanie danych z pliku
Aby odczytać dane z pliku należy użyć metody `read(x)`, gdzie x określa ile znaków z pliku odczytamy. Aby odczytać całą linię tekstu należy użyć metody `readline()`.
### Zapisywanie danych do pliku
Aby zapisać dane do pliku należy użyć metody `write(x)`, gdzie x jest danymi które dopisujemy do pliku.

```python
file = open("numbers.txt", "r+t")
old_data = file.readline()
file.write(new_data)
file.close()
```

## Obsługa wyjątków
W normalnej sytuacji jeżeli w programie wystąpi błąd, oznacza to że nastąpiła nieprzewidziana sytuacja, i dalsze kontynuowanie działania programu nie ma sensu. Program natychmiast zakańcza działanie i zwraca informację o błędzie. Czasem jednak błędy muszą być wzięte pod uwagę jako normalne zdarzenie w czasie działania, zwłaszcza jeżeli program ma wchodzić w interakcję z innymi programami, plikami, siecią czy użytkownikiem. W takim wypadku należy zaimplementować prawidłowe przywrócenie programu do działania po wystąpieniu błędu. Aby wystąpienie błędu nie zatrzymało działania programu, należy zastosować mechanizm wyjątków (*exception*). W momencie wystąpienia błędu program uruchamia specjalną procedurę, zwaną wyjątkiem, która pozwala przywrócić normalne działanie. Aby zastosować ten mechanizm, należy kod mogący "rzucić" wyjątek zamknąć w bloku *try/except*. Sekcja `try` uruchamia program, ale w razie jego awarii nie zatrzymuje się, tylko przechodzi do bloku `except`, gdzie uruchamia odpowiednią procedurę.

```python
try:
    print(x)
except:
    print("Wystąpił błąd")
```

Wyjątki mogą mieć własne nazwy, co pozwala na zareagowanie na różne rodzaje błędów które mogły wystąpić. Blok 'except' z podaną nazwą wyjątku zareaguje tylko na ten konkretny błąd, a bez podania nazwy wyjątku złapie wszystkie które pozostały. **Jeżeli wyjątek zostanie złapany, to jest usuwany. Dlatego blok `except` bez nazwy powinien być na końcu**

```python
try:
    print(x)
except NameError:
    print("brak zmiennej o podanej nazwie")
except:
    print("awaria w funkcji print")
```

Dodatkowo do bloku *try/except* można dodać bloki `else` i `finally`, które zostaną wywołane odpowiednio jeżeli błąd nie wystąpił, oraz niezależnie od tego czy wystąpił czy nie.
try -> except/else -> finally

```python
try:
    f = open("filename")
except:
    print("File opening error")
else:
    f.close()
finally:
    print("file operations completed")
```

Aby rzucić wyjątek należy użyć polecenia `raise` i jednej z dostępnych klas wyjątków, opisującej błąd. Ogólnym typem wyjątku jest klasa `Exception`, istnieją także klasy do opisu innych błędów, np.: `ValueError`, `TypeError`, `ZeroDivisionError`, `FileNotFoundError`, `NameError`, `KeyError`, `IndexError` itp. Można także stworzyć własną klasę wyjątku.

```python
def divide_object(object, number):
    if number == 0:
        raise ZeroDivisionError
    else:
        return object/number
```

## Pliki JSON
Aby wyeksportować dane należy zapisać je w pliku tekstowym. Służy do tego specjalny format plików o nazwie JavaScript Object Notation. Został on stworzony do zapisu obiektów JavaScript, ale równie dobrze nadaje się do Pythona. Aby móc go używać należy skorzystać z modułu `json`. W takim pliku można zapisywać podstawowe struktury danych Pythona, takie jak liczby całkowite i zmiennoprzecinkowe, ciągi znaków, listy i słowniki. Przykładowy plik JSON:

```json
{"menu": {
  "id": "file",
  "value": "File",
  "popup": {
    "menuitem": [
      {"value": "New", "onclick": "CreateNewDoc()"},
      {"value": "Open", "onclick": "OpenDoc()"},
      {"value": "Close", "onclick": "CloseDoc()"}
    ]
  }
}}
```

## Zadania
### Bank
1. Stwórz program bankowy który będzie pozwalał na wykonywanie podstawowych operacji finansowych. Na początku niech bank posiada jednego użytkownika. Stan konta powinien być przechowywany w specjalnie nazwanym pliku. Dodaj metody pozwalające na zwiększenie i zmniejszenie stanu konta. Program powinien zachowywać stan konta użytkownika nawet jeżeli zostanie wyłączony i włączony później.
2. Aby bank mógł przechowywać informacje o większej ilości użytkowników, zmień system przechowywania danych kont na plik JSON. Dodaj możliwość przelewów z konta jednego użytkownika na konto innego użytkownika.
3. W wypadku błędnej operacji dodaj mechanizm wyjątków który zapobiegnie wykonaniu niemożliwej operacji bankowej.
3. Dodaj system autoryzacji, który przed wykonaniem każdego przelewu będzie wymagał od użytkownika podania hasła. Hasło powinno być ustawiane w momencie utworzenia konta użytkownika.


