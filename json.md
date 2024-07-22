---
title: "Pliki JSON"
permalink: /json
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

## Pliki JSON
Aby wyeksportować dane które będą łatwe do odczytania, należy zapisać je w pliku tekstowym. Służy do tego specjalny format plików o nazwie JavaScript Object Notation. Został on stworzony do zapisu obiektów JavaScript, ale równie dobrze nadaje się do Pythona. Aby móc go używać należy skorzystać z modułu `json`. W takim pliku można zapisywać **podstawowe** struktury danych Pythona, takie jak liczby całkowite i zmiennoprzecinkowe, ciągi znaków, listy i słowniki. Przykładowy plik JSON:

```json
{
    "firstName": "Jane",
    "lastName": "Doe",
    "hobbies": ["running", "sky diving", "singing"],
    "age": 35,
    "children": [
        {
            "firstName": "Alice",
            "age": 6
        },
        {
            "firstName": "Bob",
            "age": 8
        }
    ]
}
```

**Uwaga!** w pliku JSON nie ma osobnego sposobu zapisu krotki, zostanie ona zapisana jako lista.

### Zapisywanie danych do JSON
Aby zapisać dane do formatu JSON, należy użyć metody `json.dump(data, write_file)` (do zapisania danych do pliku) lub `json_string = json.dumps(data)` (do zapisania danych do zmiennej tekstowej).

**Ważne!** W jednym pliku JSON można tylko jeden raz użyć metody `dump`, gdyż wrzucenie dwóch zbiorów danych do jednego pliku spowoduje problem z odczytem. Aby zapisać więcej niż jeden element należy zamknąć je w liście.

Aby odczytać dane z JSON do Pythona, należy użyć metody `data = json.load(read_file)` (do odczytania danych z pliku) lub `data = json.loads(json_string)` (do odczytania danych z dostępnej zmiennej tekstowej).

Przykładowy plik zajezdnie.json:

```json
{
    "Zajezdnia Nowa Huta": ["Lajkonik", "Krakowiak"],
    "Zajezdnia Podgórze": ["Akwarium", "NGT-6", "GT8"]
}
```

```python
import json

with open("zajezdnie.json") as zajezdnie_plik:
    zajezdnie = json.load(zajezdnie_plik)
    tramwaj = zajezdnie["Zajezdnia Nowa Huta"].pop()
    zajezdnie["Zajezdnia Podgórze"].append(tramwaj)
    zajezdnie.plik.truncate()
    json.dump(zajezdnie_plik, zajezdnie)
```

## Ćwiczenia
1. Napisz program który zapisze plik JSON z każdym dostępnym typem danych: liczbą stałoprzecinkową, zmiennoprzecinkową, zmienną tekstową, zmienną logiczną, listę i słownik.
2. Napisz program który będzie otwierał plik JSON, dopisywał do niego godzinę o której został otwarty, i zamykał go.

## Zadania
### Bank
[bank.py](https://github.com/APE-Krakow/tasks/blob/main/bank/bank.py)
1. Stwórz program bankowy który będzie pozwalał na wykonywanie podstawowych operacji finansowych. Na początku niech bank posiada jednego użytkownika. Stan konta powinien być przechowywany w specjalnie nazwanym pliku. Dodaj metody pozwalające na zwiększenie i zmniejszenie stanu konta. Program powinien zachowywać stan konta użytkownika nawet jeżeli zostanie wyłączony i włączony później.
2. Aby bank mógł przechowywać informacje o większej ilości użytkowników, zmień system przechowywania danych kont na plik JSON. Dodaj możliwość przelewów z konta jednego użytkownika na konto innego użytkownika.
3. W wypadku błędnej operacji dodaj mechanizm wyjątków który zapobiegnie wykonaniu niemożliwej operacji bankowej.
4. Dodaj system autoryzacji, który przed wykonaniem każdego przelewu będzie wymagał od użytkownika podania hasła. Hasło powinno być ustawiane w momencie utworzenia konta użytkownika. Procedurę wpisywania hasła zabezpiecz poprzez wyjątek.

