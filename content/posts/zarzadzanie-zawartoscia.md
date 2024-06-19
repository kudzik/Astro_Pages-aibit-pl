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

## Pola front matter

### Pole `aliases`

Pole `aliases` w front matter to tablica jednego lub więcej aliasów, gdzie każdy alias jest względnym adresem URL, który przekierowuje przeglądarkę do bieżącej lokalizacji strony.

#### Szczegóły

- **Definicja**: `aliases` służy do określania dodatkowych adresów URL, które przekierują użytkownika do aktualnej strony. Jest to przydatne, gdy chcesz mieć możliwość udostępniania strony pod różnymi URL-ami, które prowadzą do tej samej zawartości.

- **Format**: `aliases` jest tablicą stringów, gdzie każdy element to adres URL względny. Przykładem może być `aliases: ["/old-url/", "/alternate-url/"]`, gdzie każdy z tych URL-i przekierowuje do bieżącej strony.

- **Zastosowanie**: Użycie `aliases` jest szczególnie użyteczne w przypadkach zmiany struktury URL lub gdy chcesz zaktualizować istniejące linki do strony, aby nadal prowadziły do właściwej zawartości.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartości `aliases` mogą być uzyskane za pomocą metody `Aliases` na obiekcie `Page`. Można to wykorzystać do dynamicznego generowania linków lub do wyświetlania alternatywnych adresów URL w nawigacji.

- **Przykład**: Jeśli masz stronę, której URL zmienia się z `/old-url/` na `/new-url/`, możesz dodać `aliases: ["/old-url/"]` do front matter tej strony. Teraz użytkownicy, którzy używają starego linku, zostaną automatycznie przekierowani do nowego URL-a.

- **Uwaga**: Aliasowanie URL-i pozwala na zachowanie istniejących linków w przypadku zmian w strukturze strony lub adresacji URL, co może być korzystne dla SEO i użyteczności użytkownika.

Pole `aliases` jest przykładem funkcji Hugo, która wspiera zarządzanie stroną i jej dostępnością pod różnymi adresami URL, zapewniając jednocześnie elastyczność w zarządzaniu adresacją strony internetowej.

### Pole `build`

Pole `build` w front matter jest mapą opcji budowania, które dostosowują sposób w jaki Hugo renderuje i przetwarza zawartość strony.

#### Szczegóły

- **Definicja**: `build` to mapa, która zawiera opcje związane z procesem budowania strony. Jest to użyteczne do konfigurowania specyficznych parametrów renderowania i generowania zawartości strony w Hugo.

- **Format**: `build` jest mapą, gdzie klucze i wartości określają różne aspekty procesu budowania. Przykładowo, `build: { markdown: true, css: false }` mówi Hugo, aby używał renderowania markdown, ale nie generował plików CSS.

- **Zastosowanie**: Ustawienie `build` pozwala na precyzyjne zarządzanie tym, jak Hugo przetwarza poszczególne elementy strony, takie jak formaty plików, ustawienia cache, czy specjalne opcje renderowania.

- **Przykład**: Można użyć `build` do określenia, które formaty plików mają być generowane podczas budowania strony, czy włączenia lub wyłączenia określonych funkcji w zależności od potrzeb projektu.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, opcje `build` mogą być używane do dynamicznego renderowania zawartości strony w zależności od określonych warunków lub preferencji konfiguracyjnych.

- **Uwaga**: Ustawianie `build` jest przydatne szczególnie w zaawansowanych scenariuszach, gdzie chcesz dokładnie kontrolować proces budowania strony w Hugo, minimalizując zbędne operacje lub konfigurując renderowanie na potrzeby specyficznych wymagań projektowych.

Pole `build` w front matter Hugo daje użytkownikowi kontrolę nad procesem generowania i przetwarzania zawartości strony, co jest kluczowe dla optymalizacji i dostosowywania działania strony internetowej do specyficznych potrzeb projektowych.

### Pole `cascade`

Pole `cascade` to mapa kluczy, których wartości są przekazywane do potomków strony, chyba że są nadpisane przez wartości w tym samym kluczu w bieżącej stronie lub bliższym przodku w hierarchii.

#### Szczegóły

- **Definicja**: `cascade` umożliwia dziedziczenie wartości zdefiniowanych kluczy front matter przez potomne strony. Jest to przydatne do ustawiania globalnych parametrów lub wartości dla grupy stron lub sekcji, które mają wspólne cechy.

- **Format**: `cascade` jest mapą, gdzie każdy klucz reprezentuje nazwę pola front matter, a wartość tego pola jest przekazywana do wszystkich potomków strony, chyba że jest nadpisana przez potomną stronę lub bliższego przodka.

- **Zastosowanie**: Użycie `cascade` pozwala na unikanie powtarzania tych samych wartości front matter w wielu plikach, poprzez zdefiniowanie ich raz na poziomie wyższym i przekazanie ich do wszystkich odpowiednich stron potomnych.

- **Przykład**: Jeśli masz serię stron lub wpisów bloga, które mają wspólne ustawienia, takie jak `author` czy `categories`, możesz zdefiniować te wartości w `cascade` na poziomie sekcji lub rodzica i będą one dziedziczone przez wszystkie potomne strony.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartości przekazane przez `cascade` mogą być odczytywane i wykorzystywane do dynamicznego renderowania zawartości strony lub do ustalania warunków działania szablonu.

- **Uwaga**: `cascade` pomaga w utrzymaniu spójności i upraszcza zarządzanie treścią w Hugo, szczególnie w przypadku dużych projektów lub gdy wiele stron wymaga podobnych ustawień.

### Pole `date`

Pole `date` jest używane do określenia daty związanej ze stroną, zazwyczaj jest to data utworzenia. Formatowanie daty może różnić się w zależności od używanego formatu serializacji, takiego jak JSON, TOML lub YAML.

#### Szczegóły

- **Definicja**: `date` reprezentuje datę związana ze stroną lub wpisem, która często odpowiada dacie jej utworzenia lub publikacji. W Hugo daty mogą być używane do sortowania, wyświetlania lub filtrowania zawartości.

- **Format**: `date` jest zazwyczaj stringiem, który może zawierać datę w różnych formatach, np. `YYYY-MM-DD` lub `YYYY-MM-DDTHH:MM:SSZ`. TOML, specyficznie, obsługuje również daty i czasy bez cudzysłowów.

- **Zastosowanie**: Ustawienie `date` jest istotne dla strukturyzowania zawartości strony w czasie, co jest przydatne dla archiwizacji lub prezentacji treści w odpowiednim kontekście historycznym.

- **Dostęp z poziomu szablonów**: W szablonach, wartość `date` może być pobrana i przetworzona za pomocą metody `Date` na obiekcie `Page`. To umożliwia dynamiczne wykorzystanie daty do generowania interfejsu użytkownika lub dla logiki biznesowej strony.

- **Przykład**: Jeśli masz stronę z wpisem blogowym, ustawienie `date: "2024-06-19"` w front matter tej strony pomoże Hugo w odpowiednim sortowaniu i wyświetlaniu tego wpisu na liście lub kalendarium.

- **Uwaga**: `date` jest kluczowe dla zarządzania chronologią i organizacją treści w Hugo, a jego właściwe użycie ma znaczenie dla SEO, sortowania, a także dla precyzyjnego wyświetlania treści użytkownikom.

### Pole `description`

Pole `description` jest używane do określenia opisu strony, który jest zazwyczaj renderowany w elemencie meta w sekcji `<head>` opublikowanego pliku HTML.

#### Szczegóły

- **Definicja**: `description` to tekstowy opis strony, który ma za zadanie krótko i zwięźle przedstawić jej zawartość lub cel. Jest to różne od podsumowania strony (`summary`), ponieważ `description` jest przeznaczony głównie do renderowania w meta tagach na stronie internetowej.

- **Format**: `description` jest stringiem, który może zawierać do kilku zdań opisujących treść strony. Jest to zazwyczaj krótki tekst o długości odpowiedniej do wykorzystania w meta tagu `description` dla SEO.

- **Zastosowanie**: Ustawienie `description` jest ważne dla optymalizacji wyszukiwarek internetowych (SEO), ponieważ jest on często wykorzystywany przez wyszukiwarki do prezentowania opisów stron w wynikach wyszukiwania.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `description` może być pobrana i wykorzystana za pomocą metody `Description` na obiekcie `Page`. Jest to przydatne do dynamicznego generowania meta tagów lub do renderowania opisu strony na interfejsie użytkownika.

- **Przykład**: Przykładem `description` może być `"Oficjalny blog o technologiach internetowych i programowaniu"`, który krótko opisuje tematykę całego bloga lub strony.

- **Uwaga**: Dobrze sformułowany `description` może przyciągać więcej użytkowników poprzez wyniki wyszukiwania, dlatego warto zatroszczyć się o jego odpowiednią treść i długość.

### Pole `draft`

Pole `draft` w front matter jest używane do określenia, czy strona ma być uznana za wersję roboczą, która nie zostanie wyrenderowana, chyba że flaga `--buildDrafts` zostanie przekazana do polecenia `hugo`.

#### Szczegóły

- **Definicja**: `draft` jest typem boolean, który służy do oznaczania strony jako wersji roboczej lub niegotowej do publikacji. Gdy `draft` jest ustawione na `true`, strona nie jest uwzględniana w standardowym procesie renderowania strony przez Hugo.

- **Format**: `draft` jest typu boolean, czyli może przyjmować wartość `true` lub `false`. Domyślnie strony z ustawionym `draft` na `true` nie są renderowane przez Hugo, chyba że explicite uruchomisz komendę `hugo` z flagą `--buildDrafts`.

- **Zastosowanie**: Ustawienie `draft` jest przydatne, gdy tworzysz treści, które są jeszcze w fazie rozwoju lub wymagają dalszej pracy przed publikacją. Pozwala to na segregowanie wersji roboczych od gotowych do publikacji stron.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `draft` może być odczytana i wykorzystana za pomocą metody `Draft` na obiekcie `Page`. Jest to przydatne do dynamicznego zarządzania widocznością strony na interfejsie użytkownika w zależności od jej statusu.

- **Przykład**: Jeśli tworzysz nową stronę, ale nie chcesz jeszcze, aby była widoczna publicznie, możesz ustawić `draft: true` w jej front matter. Hugo nie uwzględni tej strony w generowanych plikach HTML, chyba że zdecydujesz się na renderowanie wersji roboczych.

- **Uwaga**: Zarządzanie `draft` jest pomocne dla organizacji pracy nad zawartością strony w większych projektach, gdzie ważne jest wyłącznie renderowanie gotowych do publikacji materiałów.

### Pole `expiryDate`

Pole `expiryDate` jest używane do określenia daty ważności strony, po której strona nie będzie renderowana, chyba że flaga `--buildExpired` zostanie przekazana do polecenia `hugo`.

#### Szczegóły

- **Definicja**: `expiryDate` reprezentuje datę, po której strona przestaje być ważna lub aktualna. Gdy data ważności `expiryDate` zostanie przekroczona, strona nie będzie uwzględniana w standardowym procesie generowania stron przez Hugo, chyba że użyjesz flagi `--buildExpired`.

- **Format**: `expiryDate` jest typu string, który zazwyczaj zawiera datę w formacie `YYYY-MM-DD` lub `YYYY-MM-DDTHH:MM:SSZ`. Formatowanie daty może różnić się w zależności od używanego formatu serializacji, jak JSON, TOML lub YAML.

- **Zastosowanie**: Ustawienie `expiryDate` jest przydatne, gdy masz zawartość, która jest czasowo ważna, na przykład promocje, aktualności lub inne informacje, które mają określony czas obowiązywania.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `expiryDate` może być odczytana i wykorzystana za pomocą metody `ExpiryDate` na obiekcie `Page`. Jest to przydatne do dynamicznego zarządzania widocznością strony na interfejsie użytkownika w zależności od jej daty ważności.

- **Przykład**: Jeśli publikujesz promocję, która ma obowiązywać tylko do pewnej daty, możesz ustawić `expiryDate` na `2024-12-31`, aby strona przestała być widoczna po tej dacie, chyba że użyjesz flagi `--buildExpired` do renderowania strony.

- **Uwaga**: Zarządzanie `expiryDate` jest użyteczne dla optymalizacji zawartości strony i zapewnienia, że informacje wygasające automatycznie nie będą dalej wyświetlane użytkownikom.

### Pole `headless`

Pole `headless` odnosi się do paczek (bundli) liściowych (leaf bundles). Jeśli jest ustawione na `true`, opcje renderowania i listy są ustawione na nigdy, tworząc paczkę bez głównej strony.

#### Szczegóły

- **Definicja**: `headless` jest typem boolean, który ma zastosowanie do paczek liściowych. Gdy jest ustawione na `true`, powoduje to, że opcje renderowania i listowania dla paczki są wyłączone. Oznacza to, że paczka zawiera zasoby strony, ale nie ma pojedynczej głównej strony, którą Hugo normalnie by generowało.

- **Format**: `headless` jest wartością boolean, czyli może przyjąć wartość `true` lub `false`. Domyślnie ustawione na `false`, co oznacza normalne zachowanie generowania stron przez Hugo.

- **Zastosowanie**: Ustawienie `headless` jest przydatne, gdy chcesz grupować zasoby strony bez generowania głównej strony, na przykład do przechowywania zasobów multimedialnych lub innych plików, które nie wymagają oddzielnej strony do wyświetlenia.

- **Przykład**: Jeśli tworzysz galerię obrazów w Hugo, możesz stworzyć paczkę liściową (`leaf bundle`) z ustawionym `headless: true`, aby grupować wszystkie obrazy w jednym miejscu, bez potrzeby generowania oddzielnych stron dla każdego obrazu.

- **Uwaga**: Użycie `headless` jest szczególnie przydatne w przypadku projektów wymagających organizacji i grupowania zasobów, które nie mają potrzeby posiadania tradycyjnej strony do renderowania.

### Pole `isCJKLanguage`

Pole `isCJKLanguage` służy do określenia, czy język zawartości należy do rodziny CJK (chiński, japoński, koreański). Ustawienie tego pola na `true` wpływa na sposób obliczania liczby słów oraz może mieć wpływ na wartości zwracane przez metody takie jak `WordCount`, `FuzzyWordCount`, `ReadingTime`, oraz `Summary` na obiekcie `Page`.

#### Szczegóły

- **Definicja**: `isCJKLanguage` jest typem boolean, który jest używany do oznaczenia języków z rodziny CJK, które mają inne reguły podziału słów i znaków niż języki alfabetyczne. Hugo dostosowuje sposób obliczania takich wartości jak liczba słów i czas czytania w zależności od ustawienia tego pola.

- **Format**: `isCJKLanguage` przyjmuje wartość `true` lub `false`. Domyślnie ustawione na `false`. Języki CJK charakteryzują się specyficznymi wymaganiami co do podziału słów, dlatego Hugo może potrzebować dodatkowych reguł obliczania tych parametrów.

- **Zastosowanie**: Ustawienie `isCJKLanguage` jest istotne dla precyzyjnego obliczania statystyk dotyczących tekstu w językach CJK, takich jak liczba słów, czas czytania, czy krótkie podsumowania. Umożliwia to dokładne dostosowanie wyświetlanych informacji w interfejsie użytkownika.



### Pole `slug`

Pole `slug` w front matter jest używane do nadpisywania ostatniego segmentu ścieżki URL generowanej dla danej strony. Jest to przydatne, gdy chcesz mieć kontrolę nad tym, jak konkretna strona jest adresowana w przeglądarce.

#### Szczegóły

- **Definicja**: `slug` jest ciągiem znaków (stringiem), który zastępuje ostatni segment w ścieżce URL strony. Domyślnie Hugo tworzy ścieżkę URL na podstawie tytułu lub nazwy pliku, ale możesz użyć `slug`, aby to nadpisać.

- **Zastosowanie**: Ustawiając `slug`, możesz zmienić lub uproszczyć adres URL strony, co jest przydatne zwłaszcza w przypadku stron z długimi tytułami lub gdy chcesz bardziej kontrolować strukturę URL.

- **Przykład**: Jeśli masz stronę z tytułem "Mój pierwszy wpis na blogu", to domyślnie Hugo może utworzyć URL typu `/posts/moj-pierwszy-wpis-na-blogu/`. Możesz jednak ustawić `slug` na `"moj-pierwszy-wpis"`, aby uzyskać bardziej krótki URL, np. `/posts/moj-pierwszy-wpis/`.

- **Uwaga**: Pole `slug` nie jest stosowane dla stron sekcji (np. listy postów), ponieważ Hugo automatycznie zarządza generowaniem ich URLi na podstawie nazwy sekcji i nazw plików wewnątrz sekcji.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `slug` może być uzyskana za pomocą metody `Slug` na obiekcie `Page`. Jest to przydatne do tworzenia dynamicznych linków w szablonach lub do generowania specjalnych odnośników w menu nawigacyjnym.

Pole `slug` daje użytkownikowi kontrolę nad strukturą URL danej strony, co pozwala na bardziej czytelną i optymalizowaną dla SEO adresację stron w Twoim projekcie Hugo.
