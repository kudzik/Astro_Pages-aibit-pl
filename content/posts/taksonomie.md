+++
title = 'Taksonomie'
date = 2024-06-19T18:01:56+02:00
draft = true
+++


## Taxonomie

Taxonomies w Hugo pozwalają na klasyfikację treści poprzez dodawanie terminów taksonomicznych do front matter. Na przykład w konfiguracji strony:

- **Konfiguracja Taxonomies**

```yaml
# hugo.
taxonomies:
  genre: genres
  tag: tags
```

Możesz dodać terminy taksonomiczne jak pokazano poniżej:

- **Przykład dodania terminów taksonomicznych**

```yaml
# content/example.md
---
date: 2024-02-02T04:14:54-08:00
draft: false
genres:
  - mystery
  - romance
params:
  author: John Smith
tags:
  - red
  - blue
title: Example
weight: 10
---
```

- **Rodzaje stron, do których można dodać terminy taksonomiczne**

Możesz dodawać terminy taksonomiczne do różnych rodzajów stron:

- **home** (strona główna)
- **page** (strona)
- **section** (sekcja)
- **taxonomy** (taksonomia)
- **term** (termin)

- **Dostęp do terminów taksonomicznych z poziomu szablonów**

Możesz uzyskać dostęp do terminów taksonomicznych z front matter strony za pomocą metod `Params` lub `GetTerms` na obiekcie `Page`. Na przykład:

- **Przykład użycia terminów taksonomicznych w szablonie**

```html
{{ with .GetTerms "tags" }}
  <p>Tags</p>
  <ul>
    {{ range . }}
      <li><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></li>
    {{ end }}
  </ul>
{{ end }}
```

W tym przykładzie używamy `.GetTerms "tags"` aby pobrać listę terminów z kategorii "tags" z front matter strony. Następnie używamy pętli `range` do iteracji przez każdy termin i wyświetlamy jego `LinkTitle` w formie odnośnika.
