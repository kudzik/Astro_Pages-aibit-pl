+++
title = 'Cascade'
date = 2024-06-19T18:02:57+02:00
draft = false
categories = [
   'hugo',
]
+++


## Cascade

W Hugo, każdy węzeł może przekazywać swoim potomkom zestaw wartości front matter.

### Docelowe konkretne strony

Blok `cascade` może być tablicą z opcjonalnym słowem kluczowym `_target`, pozwalającym na celowanie w różne zbiory stron podczas przekazywania wartości.

Cascade w Hugo pozwala na dziedziczenie wartości front matter pomiędzy stronami w strukturze projektu. Jest to szczególnie przydatne do ustawiania globalnych parametrów lub wartości dla grupy stron lub sekcji, które mają wspólne cechy.

#### Przykład użycia `cascade`

```yaml
# content/_index.md
cascade:
  - _target: "section"
    author: "John Doe"
    tags:
      - general
  - _target: "page"
    draft: false
```

W powyższym przykładzie `cascade` jest zdefiniowane jako tablica z dwoma elementami. Każdy element zawiera opcjonalny `_target`, który określa, do jakiego rodzaju stron powinny być przekazywane wartości front matter.

- Pierwszy element `_target: "section"` przekazuje wartości `author` i `tags` do wszystkich stron należących do sekcji.
- Drugi element `_target: "page"` ustawia wartość `draft: false` dla każdej pojedynczej strony.

Dzięki `cascade` możesz precyzyjnie zarządzać dziedziczeniem wartości, co jest przydatne przy tworzeniu dużych stron internetowych z różnorodnymi sekcjami i rodzajami stron.

