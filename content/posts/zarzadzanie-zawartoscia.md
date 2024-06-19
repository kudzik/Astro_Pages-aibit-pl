+++
title = 'Zarzadzanie Zawartoscia'
date = 2024-06-19T13:38:45+02:00
draft = true
+++

## Front matter

Użyj front matter, aby dodać metadane do swojej treści.

### Przegląd

Front matter znajdujący się na początku każdego pliku z treścią to metadane, które:

- **Opisują zawartość**: Zawierają informacje takie jak tytuł, data publikacji, autor itp.
- **Uzupełniają zawartość**: Mogą zawierać dodatkowe informacje, takie jak kategorie, tagi, streszczenia.
- **Ustalają relacje z innymi treściami**: Pozwalają na powiązanie z innymi wpisami, tworzenie hierarchii stron itp.
- **Kontrolują strukturę publikacji twojej strony**: Mogą wpływać na to, czy treść jest szkicem, kiedy ma zostać opublikowana, czy jest ukryta.
- **Określają wybór szablonu**: Mogą wskazywać, jaki szablon powinien być użyty do renderowania danej treści.

Front matter jest dostarczany w jednym z trzech formatów serializacji: JSON, TOML lub YAML. Hugo rozpoznaje format front matter, analizując delimitery, które oddzielają front matter od reszty zawartości strony.

Poniżej przedstawiamy przykłady delimiterów front matter dla różnych formatów serializacji.

### Przykłady delimiterów front matter

#### YAML

Front matter w formacie YAML jest ograniczony przez trzy kreski (`---`) na górze i na dole:

```markdown
---
title: "Mój pierwszy wpis"
date: 2024-06-19
draft: true
---
```

#### TOML

Front matter w formacie TOML jest ograniczony przez trzy znaki plus (`+++`) na górze i na dole:

```toml
+++
title = "Mój pierwszy wpis"
date = 2024-06-19
draft = true
+++
```

#### JSON

Front matter w formacie JSON jest ograniczony przez nawiasy klamrowe (`{}`) na górze i na dole:

```json
{
  "title": "Mój pierwszy wpis",
  "date": "2024-06-19",
  "draft": true
}
```

### Zastosowanie front matter

W Hugo, front matter pozwala na elastyczne zarządzanie treścią i strukturą strony. Możesz dodawać różne metadane, które będą wykorzystywane do generowania dynamicznych i dobrze zorganizowanych stron. Dzięki front matter, Hugo może łatwo klasyfikować, filtrować i renderować treści według zdefiniowanych przez ciebie kryteriów.

Przykładowy plik markdown z front matter w formacie YAML:

```markdown
---
title: "Jak używać Front Matter w Hugo"
date: 2024-06-19
author: "Jan Kowalski"
tags: ["hugo", "markdown", "tutorial"]
categories: ["Programowanie", "Web Development"]
draft: false
---
```

Pola wraz z krótkim opisem:

| Pole               | Opis                                                                                                        |
|-------------------|--------------------------------------------------------------------------------------------------------------|
| `aliases`         | Tablica aliasów URL, które przekierowują do bieżącej strony.                                                    |
| `build`           | Mapa opcji budowania strony.                                                                                   |
| `cascade`         | Mapa kluczy Front Matter, których wartości są przekazywane do stron potomnych.                                  |
| `date`           | Data związana ze stroną (zazwyczaj data utworzenia).                                                           |
| `description`    | Opis strony, często używany w meta tagach.                                                                     |
| `draft`          | Określa, czy strona jest szkicem (nie będzie publikowana domyślnie).                                            |
| `expiryDate`     | Data wygaśnięcia strony (po tej dacie strona nie będzie publikowana domyślnie).                                |
| `headless`       | Dotyczy pakietów "leaf bundles", ukrywa stronę i jej listę.                                                      |
| `isCJKLanguage`  | Określa, czy język treści należy do rodziny CJK (chiński, japoński, koreański).                                 |
| `keywords`       | Tablica słów kluczowych, często używanych w meta tagach lub taksonomiach.                                       |
| `lastmod`        | Data ostatniej modyfikacji strony.                                                                           |
| `layout`         | Nazwa szablonu używanego do renderowania strony.                                                               |
| `linkTitle`      | Zazwyczaj krótsza wersja tytułu.                                                                              |
| `markup`         | Identyfikator formatu treści (np., "markdown").                                                               |
| `menus`          | Dodaje stronę do wskazanego menu lub menu.                                                                     |
| `outputs`        | Formaty wyjściowe do renderowania.                                                                             |
| `params`         | Mapa niestandardowych parametrów strony.                                                                        |
| `publishDate`    | Data publikacji strony (przed tą datą strona nie będzie publikowana domyślnie).                                |
| `resources`      | Tablica map z metadanymi dla zasobów strony.                                                                    |
| `sitemap`        | Mapa opcji mapy witryny.                                                                                       |
| `slug`           | Nadpisuje ostatni segment ścieżki URL.                                                                         |
| `summary`        | Podsumowanie lub zajawka strony.                                                                               |
| `title`          | Tytuł strony.                                                                                                 |
| `translationKey` | Klucz używany do powiązania tłumaczeń tej samej strony.                                                           |
| `type`           | Typ treści, nadpisuje wartość pochodzącą z sekcji najwyższego poziomu.                                            |
| `url`            | Nadpisuje całą ścieżkę URL.                                                                                    |
| `weight`         | Waga strony, używana do sortowania stron w kolekcji.                                                            |