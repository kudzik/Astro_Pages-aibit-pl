+++
title = 'Podstawowe polecenia CLI'
date = 2024-06-19T12:54:25+02:00
draft = false
+++

## Linia poleceń

W tej części omówimy najczęściej używane polecenia w Hugo. Są one kluczowe do efektywnej pracy z tym frameworkiem.

### Sprawdzenie pomocy i dostępnych poleceń

Jeśli potrzebujesz więcej informacji na temat dostępnych poleceń, użyj:

```sh
hugo help
hugo server --help
```

To polecenie wyświetli listę wszystkich dostępnych poleceń oraz krótki opis każdego z nich.

### Tworzenie nowego projektu

```sh
hugo new site nazwa-projektu
```

To polecenie stworzy nowy katalog z podstawową strukturą plików Hugo.

### Uruchamianie serwera deweloperskiego

Podczas tworzenia treści możesz chcieć na bieżąco podglądać, jak wygląda twoja strona. Aby uruchomić serwer deweloperski, użyj:

```sh
hugo server
```

Serwer będzie dostępny pod adresem `http://localhost:1313/`. Strona automatycznie odświeży się po wprowadzeniu zmian w plikach.

### Uruchamianie serwera deweloperskiego z uwzględnieniem szkiców

Podczas tworzenia treści możesz chcieć na bieżąco podglądać, jak wygląda twoja strona. Aby uruchomić serwer deweloperski i jednocześnie uwzględnić szkice (drafty) w podglądzie, użyj:

```sh
hugo server -D
```

Opcja `-D` (lub `--buildDrafts`) sprawia, że Hugo generuje stronę wraz ze wszystkimi szkicami, które normalnie nie byłyby widoczne na stronie produkcyjnej. Serwer będzie dostępny pod adresem `http://localhost:1313/`. Strona automatycznie odświeży się po wprowadzeniu zmian w plikach.

Użycie tego polecenia jest szczególnie przydatne podczas pisania nowych postów, które oznaczone są jako szkice i nie są jeszcze gotowe do publikacji.

### Uruchamianie serwera deweloperskiego z automatycznym przenoszeniem na edytowaną stronę

Flagę `--navigateToChanged` używa się podczas uruchamiania serwera deweloperskiego Hugo w celu automatycznego przenoszenia przeglądarki do zmienionych stron lub plików podczas ich edycji. Zmienia to domyślne zachowanie, które polega na ręcznym odświeżaniu strony lub przewijaniu do zmienionych plików w przeglądarce.

```sh
     hugo server --navigateToChanged
```

### Tworzenie nowego wpisu

Aby dodać nowy wpis na bloga, użyj:

```sh
hugo new posts/nazwa-wpisu.md
```

To polecenie stworzy nowy plik markdown w katalogu `content/posts`, gdzie będziesz mógł napisać treść swojego wpisu.

### Generowanie statycznej strony

Gdy twoja strona jest gotowa, możesz wygenerować statyczne pliki HTML:

```sh
hugo
```

Pliki zostaną zapisane w katalogu `public/`, skąd możesz je wdrożyć na serwer.

### Podgląd wersji Hugo

Aby sprawdzić, którą wersję Hugo masz zainstalowaną, użyj:

```sh
hugo version
```

To polecenie wyświetli aktualną wersję Hugo, która jest zainstalowana na twoim komputerze.
