+++
title = 'Struktura katalogów w Hugo'
date = 2024-06-19T18:43:38+02:00
draft = false
categories = ['hugo']
summary = 'W tym artykule przyjrzymy się podstawowej strukturze katalogów w projekcie Hugo. Omówimy funkcje poszczególnych katalogów.Ten przewodnik pomoże początkującym, użytkownikom lepiej zrozumieć, jak organizować swoje projekty w Hugo.'
+++


Struktura katalogów w Hugo jest elastyczna i umożliwia łatwe zarządzanie treściami i szablonami. W tym artykule przyjrzymy się podstawowej strukturze katalogów w projekcie i wyjaśnimy, jak każdy z katalogów może być używany.

### Podstawowa struktura katalogów

Po utworzeniu nowego projektu Hugo za pomocą polecenia `hugo new site mysite`, otrzymujemy następującą strukturę katalogów:

```text
mysite/
├── archetypes/
├── assets/
├── content/
├── data/
├── layouts/
├── public/
├── resources/
├── static/
├── themes/
└── config.toml
```

Każdy z tych katalogów pełni określoną funkcję:

### Katalog `archetypes/`

Katalog `archetypes/` zawiera domyślne szablony dla nowych treści. Szablony te definiują strukturę i domyślne wartości front matter dla nowych plików tworzonych za pomocą polecenia `hugo new`. Przykładowy plik archetypu `default.md` może wyglądać tak:

```markdown
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
---
```

### Katalog `assets/`

Katalog `assets/` jest używany do przechowywania plików, które będą przetwarzane przez Hugo Pipes, takich jak pliki CSS/SCSS, JavaScript czy obrazy. Pozwala to na zaawansowane przetwarzanie zasobów, takie jak minifikacja, kompresja czy łączenie plików.

### Katalog `content/`

Katalog `content/` to miejsce, gdzie przechowywane są wszystkie treści Twojej strony, takie jak wpisy na blogu, strony informacyjne czy portfolio. Struktura tego katalogu może odzwierciedlać strukturę URL Twojej strony:

```text
content/
├── about.md
├── blog/
│   ├── first-post.md
│   └── second-post.md
└── projects/
    ├── project1.md
    └── project2.md
```

### Katalog `data/`

Katalog `data/` służy do przechowywania danych w formatach JSON, TOML lub YAML, które mogą być używane w szablonach Hugo. Przykładem może być lista członków zespołu, którą można łatwo załadować i wyświetlić na stronie.

### Katalog `layouts/`

Katalog `layouts/` zawiera wszystkie szablony używane do renderowania treści. To tutaj znajdują się pliki takie jak `single.html`, `list.html` czy `index.html`, które definiują układ i wygląd stron.

### Katalog `public/`

Katalog `public/` jest miejscem, gdzie Hugo generuje statyczne pliki HTML. Jest to katalog, który przesyłasz na serwer, aby opublikować swoją stronę. Zawartość tego katalogu jest nadpisywana za każdym razem, gdy uruchomisz polecenie `hugo`.

### Katalog `resources/`

Katalog `resources/` jest używany przez Hugo do przechowywania zasobów przetworzonych przez Hugo Pipes. Jest to katalog wewnętrzny, który pomaga w zarządzaniu przetworzonymi plikami.

### Katalog `static/`

Katalog `static/` zawiera pliki, które są kopiowane bez zmian do katalogu `public/`. Są to zazwyczaj pliki takie jak obrazy, pliki CSS czy JavaScript, które nie wymagają przetwarzania.

### Katalog `themes/`

Katalog `themes/` przechowuje motywy używane w Twojej stronie Hugo. Możesz mieć wiele motywów i przełączać się między nimi, modyfikując plik konfiguracyjny `config.toml`.

### Plik `config.toml`

Plik `config.toml` to główny plik konfiguracyjny Twojej strony Hugo. Określa on takie ustawienia jak tytuł strony, język, URL bazy, konfiguracje menu, parametry globalne i wiele innych. Możesz również użyć formatu YAML (`config.yaml`) lub JSON (`config.json`).
