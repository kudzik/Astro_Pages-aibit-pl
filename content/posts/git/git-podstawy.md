+++
title = 'Git Podstawy'
date = 2024-06-22T07:41:36+02:00
draft = true
+++



Typowy przepływ pracy z Git:

1. Inicjalizacja lub klonowanie repozytorium:
   - Jeśli zaczynasz nowy projekt: `git init`
   - Jeśli dołączasz do istniejącego projektu: `git clone [adres_repozytorium]`

2. Stworzenie nowej gałęzi dla funkcjonalności:
   - `git branch nowa-funkcja`
   - `git checkout nowa-funkcja`
   (lub w skrócie: `git checkout -b nowa-funkcja`)

3. Praca nad funkcjonalnością:
   - Edycja plików
   - Dodawanie nowych plików

4. Sprawdzenie statusu zmian:
   - `git status`

5. Dodanie zmian do poczekalni (staging area):
   - `git add [nazwa_pliku]` lub `git add .` (dla wszystkich zmian)

6. Zatwierdzenie zmian (commit):
   - `git commit -m "Opis wprowadzonych zmian"`

7. Powtarzanie kroków 3-6 aż do ukończenia funkcjonalności

8. Aktualizacja gałęzi głównej (zwykle master lub main):
   - `git checkout master`
   - `git pull origin master`

9. Połączenie gałęzi funkcjonalności z gałęzią główną:
   - `git merge nowa-funkcja`
   (lub stworzenie pull requesta w przypadku korzystania z platform jak GitHub)

10. Rozwiązanie ewentualnych konfliktów

11. Wysłanie zmian do zdalnego repozytorium:
    - `git push origin master`

12. Usunięcie niepotrzebnej już gałęzi funkcjonalności:
    - `git branch -d nowa-funkcja`

Ten przepływ pracy zapewnia, że:

- Pracujesz na oddzielnej gałęzi, nie zakłócając pracy głównej gałęzi projektu.
- Twoje zmiany są logicznie pogrupowane w commity.
- Przed połączeniem zmian z główną gałęzią, upewniasz się, że masz najnowszą wersję kodu.
- Zmiany są regularnie synchronizowane ze zdalnym repozytorium.
