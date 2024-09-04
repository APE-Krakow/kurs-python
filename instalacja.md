---
title: "Instalacja"
permalink: /instalacja
theme: jekyll-theme-tactile
---

[Wróć do strony głównej](index.md)

Aby rozpocząć przygodę z programowaniem, musimy wiedzieć gdzie programy będą uruchamiane - w systemie operacyjnym. Główne systemy do wybory to Windows, Linux i MacOs (Mac jest bardzo podobny do Linuxa).

## Linux

Najbardziej polecam korzystanie z systemu operacyjnego Linux zamiast Windowsa, ponieważ jeżeli potem przejdziemy np. do budowania programów internetowych, to będziemy musieli obsługiwać też serwery internetowe które działają prawie wyłącznie na Linuxie, więc dobrze jest mieć doświadczenie. Nie trzeba usuwać swojego Windowsa, można zainstalować dwa systemy na jednym dysku lub mieć Linuxa na maszynie wirtualnej (oczywiście można też korzystać z Windowsa, ale ostrzegam że Windows jest dużo bardziej toporny do programowania).

[pobieranie Virtualbox](https://www.virtualbox.org/wiki/Downloads)

Istnieje mnóstwo wersji Linuxa, ale generalnie różnią się tylko wyglądem i programami dostępnymi na start. Najłatwiejsze w uruchomieniu jest Ubuntu:

[pobieranie Ubuntu](https://ubuntu.com/download)

Aby zainstalować maszynę trzeba w Virtualboxie kliknąć przycisk `+` i wybrać obraz systemu który pobraliśmy. Następnie samouczek przeprowadzi nas przez wszystkie opcje.

Po uruchomieniu Ubuntu należy uruchomić terminal skrótem **ctrl + alt + t**, a następnie wpisać następujące polecenia:

```shell
sudo apt update
sudo apt upgrade
sudo apt install python3 python-is-python3
```

## Windows/Mac

Aby zainstalować Pythona należy wejść na stronę [python.org](https://www.python.org/downloads/), wybrać swoją wersję systemu, pobrać instalator i uruchomić go.

**Należy zaznaczyć checkbox 'add to system path'**

## Edytor
Aby edytować programy można korzystać z dowolnego edytora tekstu, na
przykład:
- [Visual Studio Code](https://code.visualstudio.com/)
- [PyCharm](https://www.jetbrains.com/pycharm/)
- [Sublime Text](https://www.sublimetext.com/)
- [Notepad++](https://notepad-plus-plus.org/)

Na początek najwygodniejszy może być Thonny - nie ma zbyt wiele funkcji które rozpraszają użytkownika:
[Thonny](https://thonny.org/)

