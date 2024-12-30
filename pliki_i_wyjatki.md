---
title: "Pliki i Wyjątki"
permalink: /pliki
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

<https://docs.python.org/3/library/functions.html#open>
<https://docs.python.org/3/library/exceptions.html>

## Pliki

### Otwieranie pliku

Aby móc zapisywać dane do pliku, plik należy najpierw otworzyć za pomocą funkcji `open(nazwa_pliki, tryb_dostępu)`. Po otwarciu pliku otrzymujemy _uchwyt_ do pliku, czyli wskaźnik na dane miejsce w pliku, które pozwala na odczytywanie lub zapisywanie do niego. Uchwyt do pliku można traktować jako kursor. Każda operacja przesuwa ten wskaźnik o tyle znaków ile zostało użytych w poleceniu. Tryb dostępu określa w jaki sposób będzie zachowywał się plik i w którym miejscu zostanie umieszczony uchwyt:

- `r` (read only) - plik tylko do odczytu. Uchwyt jest umieszczany na początku pliku. Jest to domyślny tryb dostępu
- `w` (write only) - plik tylko do zapisu. Jeżeli plik wcześniej nie istniał to zostanie utworzony. Jeżeli plik wcześniej istniał to jego zawartość zostaje usunięta. Uchwyt jest umieszczany na początku pliku.
- `a` (append only) - plik do dopisu. Nowe dane będą umieszczone na końcu pliku. Jeżeli plik wcześniej nie istniał to zostanie utworzony.

Jeżeli do nazwy trybu dodamy `+`, to pozwoli on na wszystkie operacje (np. tryb r+ pozwoli również na zapis)

Dodatkowo plik można otworzyć jako:

- `t` - plik tekstowy (domyślnie) - tekst czytelny dla człowieka
- `b` - plik binarny - dane w formie zer i jedynek czytelne tylko dla innych programów

Tryby otwarcia pliku można łączyć, tworząc różne kombinacje, na przykład:

- `rt` - plik tekstowy do odczytu
- `r+b` - plik binarny do odczytu i zapisu
- `wt` - plik tekstowy do zapisu

Należy pamiętać aby po zakończeniu obsługi pliku zamknąć go metodą `close()`.

```python
file = open("database.txt", "rt")
file.close()
```

**Uwaga!** Należy unikać otwarcia kilku uchwytów na raz, ponieważ może to spowodować zapisywanie jednocześnie kilku rzeczy w tym samym miejscu

### Odczytywanie danych z pliku

Metoda `read(size)` służy do odczytywania danych z pliku. Domyślnie odczytuje cały plik, ale można podać jako jej argument liczbę znaków którą ma odczytać. Aby odczytać tylko jedną linię tekstu można użyć metody `readline(size)`. Tutaj również można podać maksymalną ilość znaków która ma być odczytana. Z kolei metoda `readlines()` odczyta wszystkie linie tekstu i zapisze je w liście.

### Zapisywanie danych do pliku

Aby zapisać dane do pliku należy użyć metody `write(x)`, gdzie x jest danymi które dopisujemy do pliku.

**Uwaga!** Ze względu na wewnętrzny mechanizm odczytu, po odczytaniu tylko części pliku i przejściu do zapisu, uchwyt i tak przeniesie się na koniec dlatego zazwyczaj najlepiej jest ręcznie pozycjonować kursor przez zapisem.

```python
file = open("numbers.txt", "r+t")
old_data = file.readline()
file.write(new_data)
file.close()
```

### Usuwanie danych z pliku

Aby usunąć dane, należy użyć metody `truncate()`. Metoda ta działa tak samo jak `read(x)` - argument `x` określa ilość znaków do usunięcia, a w wypadku pozostawienia pustego pola usuwany jest cały plik.

### Przesuwanie uchwytu

Do przesuwania uchwytu w pliku bez zmieniania jego zawartości służy metoda `seek(start, przesunięcie)`. Jako start należy podać z którego miejsca chcemy zacząć przesunięcie, a następnie podać o ile chcemy przesunąć uchwyt. Metoda ta nie pozwala jednak przesuwać się w tył pliku.

Możemy wybrać jeden z trzech punktów początkowych:

- 0 - początek pliku
- 1 - obecna pozycja w pliku
- 2 - koniec pliku

Aby przesunąć uchwyt na początek pliku wystarczy użyć metody `seek(0,0)`, a na koniec `seek(2,0)`.

Do odczytania bieżącej pozycji uchwytu służy metoda `tell()`.

Aby odczytać liczbę z pliku a następnie powiększyć ją o jeden i zapisać znowu, można się posłużyć następującym kodem:

```python
file = open("secret_number.txt", "r+t")
old_number = int(file.read())
file.seek(0,0)
file.truncate()
file.write(str(old_number+1))
file.close()
```

## Obsługa wyjątków

W normalnej sytuacji jeżeli w programie wystąpi błąd, oznacza to że nastąpiła nieprzewidziana sytuacja, i dalsze kontynuowanie działania programu nie ma sensu. Program natychmiast zakańcza działanie i zwraca informację o błędzie. Czasem jednak błędy muszą być wzięte pod uwagę jako normalne zdarzenie w czasie działania, zwłaszcza jeżeli program ma wchodzić w interakcję z innymi programami, plikami, siecią czy użytkownikiem. W takim wypadku należy zaimplementować prawidłowe przywrócenie programu do działania po wystąpieniu błędu. Aby wystąpienie błędu nie zatrzymało działania programu, należy zastosować mechanizm wyjątków (_exception_). W momencie wystąpienia błędu program uruchamia specjalną procedurę, zwaną wyjątkiem, która pozwala przywrócić normalne działanie. Aby zastosować ten mechanizm, należy kod mogący "rzucić" wyjątek zamknąć w bloku _try/except_. Sekcja `try` uruchamia program, ale w razie jego awarii nie zatrzymuje się, tylko przechodzi do bloku `except`, gdzie uruchamia odpowiednią procedurę.

```python
try:
    print(x)
except:
    print("Wystąpił błąd w funkcji print")
# dalszy ciąg programu wykonuje się bez zakłóceń
```

Wyjątki mogą mieć własne nazwy, co pozwala na zareagowanie na różne rodzaje błędów które mogły wystąpić. Blok 'except' z podaną nazwą wyjątku zareaguje tylko na ten konkretny błąd, a bez podania nazwy wyjątku złapie wszystkie które pozostały. **Jeżeli wyjątek zostanie złapany, to jest usuwany. Dlatego blok `except` bez nazwy powinien być na końcu** Dodatkowo pusty `except` powinien być rzadkością, ponieważ wszystkie możliwe błędy powinny być znane przed uruchomieniem programu.

```python
try:
    print(x)
except NameError:
    print("brak zmiennej o podanej nazwie")
except:
    print("nieznana awaria w funkcji print")
```

Dodatkowo do bloku _try/except_ można dodać bloki `else` i `finally`, które zostaną wywołane odpowiednio jeżeli błąd nie wystąpił, oraz niezależnie od tego czy wystąpił czy nie.
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

### Zabezpieczanie zasobu

Aby otworzyć jakiś zasób (plik, port sieciowy itp.) w sposób gwarantujący bezpieczne rozwiązanie błędów i automatyczne zamknięcie zasobu, można użyć słowa kluczowego `with`. Tworzy on osobny blok kodu w którym możemy korzystać z zasobu, a po jego opuszczeniu zasób jest zamykany. Zapobiega to błędom związanym z nieprawidłowym zamknięciem zasobu jeżeli w czasie obsługi pliku wystąpi błąd. Jeżeli w bloku `with` wystąpi wyjątek, nadal powinno się go obsłużyć. Dodatkowo można użyć słowa kluczowego `as`, by nadać własną nazwę zasobowi.

```python
with open("database.txt", "r+") as data:
    data.write(...)
```

Na końcu bloku `with` nie ma potrzeby zamykać pliku gdyż dzieje się to automatycznie.

## Ćwiczenia:

1. Stwórz w notatniku plik z kilkoma imionami, możesz nazwać go `imiona.txt`. Następnie stwórz program który go otworzy i zamknie.
2. Odczytaj z pliku kilka pierwszych imion i wypisz je na ekranie.
3. Zapisz w pliku jakieś nowe imię.
4. Usuń ostatnie imię z pliku.
5. Przesuń kursor do środka pliku i zapisz tam nowe imię.
6. Obsłuż wyjątek który mógłby wystąpić gdyby plik który chcemy otworzyć nie istniał.

## Zadania

### Zaszyfrowany plik

1. Napisz program do tworzenia zaszyfrowanych wiadomości. Użytkownik powinien podać zwykłą wiadomość tekstową, a program powinien ją zaszyfrować w dowolny sposób i zapisać do pliku. Metoda szyfrowania może być dowolna (np. wstawianie co drugi znak losowego znaku tekstowego).
2. Napisz program deszyfrujący wiadomości z poprzedniego podpunktu.
3. Dodaj do obu programów procedury obsługi wyjątków.

### Zajezdnia

1. Stwórz własne klasy które będą reprezentować zajezdnię tramwajową oraz tramwaje. Przeciąż metody `__add__` i `__sub__` aby móc dodawać i zabierać tramwaje z zajezdni. Opis przeciążania dodawania i odejmowania znajduje się [tutaj](dodatek.md).
2. Dodaj obsługę wyjątków która zapewni że nie będzie można wykonać niemożliwych operacji matematycznych.

## Projekt

Do gry możemy dodac system umożliwiający zapamiętanie np. najwyższej ilości punktów zdobytych przez gracza.

1. Dodaj system który będzie przyznawał punkty na zakończenie gry, np. za zcas przejścia, ilośc przedmiotów, zachowane hp.
2. Stwórz plik w którym będzie przechowywana rekordowa liczba punktów zdobyta w grze. Po zakończeniu gry sprawdź czy nowa ilośc punktów nie przewyższyła starej i zapisz ją.
3. Stwórz system radzenia sobie z wyjątkami, np. w wypadku braku pliku.
