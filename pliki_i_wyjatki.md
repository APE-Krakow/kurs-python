# Pliki i wyjątki
## Otwieranie pliku
Aby móc zapisywać dane do pliku, plik należy najpierw otworzyć za pomocą funkcji `open(nazwa_pliki, tryb_dostępu)`. Tryb dostępu określa w jaki sposób będzie zachowywał się plik:

- r (read only) - plik tylko do odczytu. Jest to domyślny tryb dostępu
- r+ (read and write) - plik do odczytu i zapisu
- w (write only) - plik tylko do zapisu. Jeżeli plik wcześniej nie istniał to zostanie utworzony.
- w+ (write and read) - plik do zapisu i odczytu. 
- a (append only) - plik do dopisu. Nowe dane będą umieszczone na końcu pliku. Jeżeli plik wcześniej nie istniał to zostanie utworzony.
- a+ (append and read) - plik do dopisu i odczytu. Nowe dane będą umieszczone na końcu pliku. Jeżeli plik wcześniej nie istniał to zostanie utworzony.

Należy pamiętać aby po zakończeniu obsługi pliku zamknąć go metodą `close()`.

## Odczytywanie danych z pliku
Aby odczytać dane z pliku należy użyć metody `read()`
## Zapisywanie danych do pliku
Aby zapisać dane do pliku należy użyć metody `write()`

## Obsługa wyjątków
W normalnej sytuacji jeżeli w programie wystąpi błąd, oznacza to że nastąpiła nieprzewidziana sytuacja, i dalsze kontynuowanie działania programu nie ma sensu. Program natychmiast zakańcza działanie i zwraca informację o błędzie. Czasem jednak błędy muszą być wzięte pod uwagę jako normalne zdarzenie w czasie działania, zwłaszcza jeżeli program ma wchodzić w interakcję z innymi programami, plikami, siecią czy użytkownikiem. W takim wypadku należy zaimplementować prawidłowe przywrócenie programu do działania po wystąpieniu błędu. Aby wystąpienie błędu nie zatrzymało działania programu, należy zastosować mechanizm wyjątków (*exception*). W momencie wystąpienia błędu program uruchamia specjalną procedurę, zwaną wyjątkiem, która pozwala przywrócić normalne działanie. Aby zastosować ten mechanizm, należy kod mogący "rzucić" wyjątek zamknąć w bloku *try/except*. Sekcja `try` uruchamia program, ale w razie jego awarii nie zatrzymuje się, tylko przechodzi do bloku `except`, gdzie uruchamia odpowiednią procedurę.

```
try:
    print(x)
except:
    print("Wystąpił błąd")
```

Wyjątki mogą mieć własne nazwy, co pozwala na zareagowanie na różne rodzaje błędów które mogły wystąpić. Blok 'except' z podaną nazwą wyjątku zareaguje tylko na ten konkretny błąd, a bez podania nazwy wyjątku złapie wszystkie które pozostały. **Jeżeli wyjątek zostanie złapany, to jest usuwany. Dlatego blok `except` bez nazwy powinien być na końcu**

```
try:
    print(x)
except NameError:
    print("brak zmiennej o podanej nazwie")
except:
    print("awaria w funkcji print")
```

Dodatkowo do bloku *try/except* można dodać bloki `else` i `finally`, które zostaną wywołane odpowiednio jeżeli błąd nie wystąpił, oraz niezależnie od tego czy wystąpił czy nie.
try -> except/else -> finally

```
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

```
def divide_object(object, number):
    if number == 0:
        raise ZeroDivisionError
    else:
        return object/number
```

## Pliki JSON
Aby wyeksportować dane należy zapisać je w pliku tekstowym. Służy do tego specjalny format plików o nazwie JavaScript Object Notation. Został on stworzony do zapisu obiektów JavaScript, ale równie dobrze nadaje się do Pythona. Aby móc go używać należy skorzystać z modułu `json`. Przykładowy plik JSON:

```
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


