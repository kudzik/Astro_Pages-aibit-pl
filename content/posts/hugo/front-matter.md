+++
title = 'Front Matter'
date = 2024-06-19T13:38:45+02:00
draft = false
categories = [
   'hugo',
]
summary = "Ukryta Moc Metadanych Czy zastanawiałeś się kiedyś, jak twórcy stron internetowych i blogów organizują swoje treści, kontrolują ich wygląd i ułatwiają nawigację? Odpowiedzią jest Front Matter niepozorny, ale potężny element, który kryje się na początku każdego pliku."
+++

## Front matter

To sekcja w plikach źródłowych używanych w różnych systemach zarządzania treścią (CMS) i generatorach statycznych stron internetowych, takich jak Hugo. Jest to część pliku umieszczona na początku, zazwyczaj pomiędzy specjalnymi delimiterami (np. ---), która zawiera metadane związane z daną stroną lub wpisem.

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

- **Definicja**: `build` to mapa, która zawiera opcje związane z procesem budowania strony. Jest to użyteczne do konfigurowania specyficznych parametrów renderowania i generowania zawartości strony w Hugo.

- **Format**: `build` jest mapą, gdzie klucze i wartości określają różne aspekty procesu budowania. Przykładowo, `build: { markdown: true, css: false }` mówi Hugo, aby używał renderowania markdown, ale nie generował plików CSS.

- **Zastosowanie**: Ustawienie `build` pozwala na precyzyjne zarządzanie tym, jak Hugo przetwarza poszczególne elementy strony, takie jak formaty plików, ustawienia cache, czy specjalne opcje renderowania.

- **Przykład**: Można użyć `build` do określenia, które formaty plików mają być generowane podczas budowania strony, czy włączenia lub wyłączenia określonych funkcji w zależności od potrzeb projektu.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, opcje `build` mogą być używane do dynamicznego renderowania zawartości strony w zależności od określonych warunków lub preferencji konfiguracyjnych.

- **Uwaga**: Ustawianie `build` jest przydatne szczególnie w zaawansowanych scenariuszach, gdzie chcesz dokładnie kontrolować proces budowania strony w Hugo, minimalizując zbędne operacje lub konfigurując renderowanie na potrzeby specyficznych wymagań projektowych.

Pole `build` w front matter Hugo daje użytkownikowi kontrolę nad procesem generowania i przetwarzania zawartości strony, co jest kluczowe dla optymalizacji i dostosowywania działania strony internetowej do specyficznych potrzeb projektowych.

### Pole `cascade`

Pole `cascade` to mapa kluczy, których wartości są przekazywane do potomków strony, chyba że są nadpisane przez wartości w tym samym kluczu w bieżącej stronie lub bliższym przodku w hierarchii.

- **Definicja**: `cascade` umożliwia dziedziczenie wartości zdefiniowanych kluczy front matter przez potomne strony. Jest to przydatne do ustawiania globalnych parametrów lub wartości dla grupy stron lub sekcji, które mają wspólne cechy.

- **Format**: `cascade` jest mapą, gdzie każdy klucz reprezentuje nazwę pola front matter, a wartość tego pola jest przekazywana do wszystkich potomków strony, chyba że jest nadpisana przez potomną stronę lub bliższego przodka.

- **Zastosowanie**: Użycie `cascade` pozwala na unikanie powtarzania tych samych wartości front matter w wielu plikach, poprzez zdefiniowanie ich raz na poziomie wyższym i przekazanie ich do wszystkich odpowiednich stron potomnych.

- **Przykład**: Jeśli masz serię stron lub wpisów bloga, które mają wspólne ustawienia, takie jak `author` czy `categories`, możesz zdefiniować te wartości w `cascade` na poziomie sekcji lub rodzica i będą one dziedziczone przez wszystkie potomne strony.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartości przekazane przez `cascade` mogą być odczytywane i wykorzystywane do dynamicznego renderowania zawartości strony lub do ustalania warunków działania szablonu.

- **Uwaga**: `cascade` pomaga w utrzymaniu spójności i upraszcza zarządzanie treścią w Hugo, szczególnie w przypadku dużych projektów lub gdy wiele stron wymaga podobnych ustawień.

### Pole `date`

Pole `date` jest używane do określenia daty związanej ze stroną, zazwyczaj jest to data utworzenia. Formatowanie daty może różnić się w zależności od używanego formatu serializacji, takiego jak JSON, TOML lub YAML.

- **Definicja**: `date` reprezentuje datę związana ze stroną lub wpisem, która często odpowiada dacie jej utworzenia lub publikacji. W Hugo daty mogą być używane do sortowania, wyświetlania lub filtrowania zawartości.

- **Format**: `date` jest zazwyczaj stringiem, który może zawierać datę w różnych formatach, np. `YYYY-MM-DD` lub `YYYY-MM-DDTHH:MM:SSZ`. TOML, specyficznie, obsługuje również daty i czasy bez cudzysłowów.

- **Zastosowanie**: Ustawienie `date` jest istotne dla strukturyzowania zawartości strony w czasie, co jest przydatne dla archiwizacji lub prezentacji treści w odpowiednim kontekście historycznym.

- **Dostęp z poziomu szablonów**: W szablonach, wartość `date` może być pobrana i przetworzona za pomocą metody `Date` na obiekcie `Page`. To umożliwia dynamiczne wykorzystanie daty do generowania interfejsu użytkownika lub dla logiki biznesowej strony.

- **Przykład**: Jeśli masz stronę z wpisem blogowym, ustawienie `date: "2024-06-19"` w front matter tej strony pomoże Hugo w odpowiednim sortowaniu i wyświetlaniu tego wpisu na liście lub kalendarium.

- **Uwaga**: `date` jest kluczowe dla zarządzania chronologią i organizacją treści w Hugo, a jego właściwe użycie ma znaczenie dla SEO, sortowania, a także dla precyzyjnego wyświetlania treści użytkownikom.

### Pole `description`

Pole `description` jest używane do określenia opisu strony, który jest zazwyczaj renderowany w elemencie meta w sekcji `<head>` opublikowanego pliku HTML.

- **Definicja**: `description` to tekstowy opis strony, który ma za zadanie krótko i zwięźle przedstawić jej zawartość lub cel. Jest to różne od podsumowania strony (`summary`), ponieważ `description` jest przeznaczony głównie do renderowania w meta tagach na stronie internetowej.

- **Format**: `description` jest stringiem, który może zawierać do kilku zdań opisujących treść strony. Jest to zazwyczaj krótki tekst o długości odpowiedniej do wykorzystania w meta tagu `description` dla SEO.

- **Zastosowanie**: Ustawienie `description` jest ważne dla optymalizacji wyszukiwarek internetowych (SEO), ponieważ jest on często wykorzystywany przez wyszukiwarki do prezentowania opisów stron w wynikach wyszukiwania.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `description` może być pobrana i wykorzystana za pomocą metody `Description` na obiekcie `Page`. Jest to przydatne do dynamicznego generowania meta tagów lub do renderowania opisu strony na interfejsie użytkownika.

- **Przykład**: Przykładem `description` może być `"Oficjalny blog o technologiach internetowych i programowaniu"`, który krótko opisuje tematykę całego bloga lub strony.

- **Uwaga**: Dobrze sformułowany `description` może przyciągać więcej użytkowników poprzez wyniki wyszukiwania, dlatego warto zatroszczyć się o jego odpowiednią treść i długość.

### Pole `draft`

Pole `draft` w front matter jest używane do określenia, czy strona ma być uznana za wersję roboczą, która nie zostanie wyrenderowana, chyba że flaga `--buildDrafts` zostanie przekazana do polecenia `hugo`.

- **Definicja**: `draft` jest typem boolean, który służy do oznaczania strony jako wersji roboczej lub niegotowej do publikacji. Gdy `draft` jest ustawione na `true`, strona nie jest uwzględniana w standardowym procesie renderowania strony przez Hugo.

- **Format**: `draft` jest typu boolean, czyli może przyjmować wartość `true` lub `false`. Domyślnie strony z ustawionym `draft` na `true` nie są renderowane przez Hugo, chyba że explicite uruchomisz komendę `hugo` z flagą `--buildDrafts`.

- **Zastosowanie**: Ustawienie `draft` jest przydatne, gdy tworzysz treści, które są jeszcze w fazie rozwoju lub wymagają dalszej pracy przed publikacją. Pozwala to na segregowanie wersji roboczych od gotowych do publikacji stron.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `draft` może być odczytana i wykorzystana za pomocą metody `Draft` na obiekcie `Page`. Jest to przydatne do dynamicznego zarządzania widocznością strony na interfejsie użytkownika w zależności od jej statusu.

- **Przykład**: Jeśli tworzysz nową stronę, ale nie chcesz jeszcze, aby była widoczna publicznie, możesz ustawić `draft: true` w jej front matter. Hugo nie uwzględni tej strony w generowanych plikach HTML, chyba że zdecydujesz się na renderowanie wersji roboczych.

- **Uwaga**: Zarządzanie `draft` jest pomocne dla organizacji pracy nad zawartością strony w większych projektach, gdzie ważne jest wyłącznie renderowanie gotowych do publikacji materiałów.

### Pole `expiryDate`

Pole `expiryDate` jest używane do określenia daty ważności strony, po której strona nie będzie renderowana, chyba że flaga `--buildExpired` zostanie przekazana do polecenia `hugo`.

- **Definicja**: `expiryDate` reprezentuje datę, po której strona przestaje być ważna lub aktualna. Gdy data ważności `expiryDate` zostanie przekroczona, strona nie będzie uwzględniana w standardowym procesie generowania stron przez Hugo, chyba że użyjesz flagi `--buildExpired`.

- **Format**: `expiryDate` jest typu string, który zazwyczaj zawiera datę w formacie `YYYY-MM-DD` lub `YYYY-MM-DDTHH:MM:SSZ`. Formatowanie daty może różnić się w zależności od używanego formatu serializacji, jak JSON, TOML lub YAML.

- **Zastosowanie**: Ustawienie `expiryDate` jest przydatne, gdy masz zawartość, która jest czasowo ważna, na przykład promocje, aktualności lub inne informacje, które mają określony czas obowiązywania.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `expiryDate` może być odczytana i wykorzystana za pomocą metody `ExpiryDate` na obiekcie `Page`. Jest to przydatne do dynamicznego zarządzania widocznością strony na interfejsie użytkownika w zależności od jej daty ważności.

- **Przykład**: Jeśli publikujesz promocję, która ma obowiązywać tylko do pewnej daty, możesz ustawić `expiryDate` na `2024-12-31`, aby strona przestała być widoczna po tej dacie, chyba że użyjesz flagi `--buildExpired` do renderowania strony.

- **Uwaga**: Zarządzanie `expiryDate` jest użyteczne dla optymalizacji zawartości strony i zapewnienia, że informacje wygasające automatycznie nie będą dalej wyświetlane użytkownikom.

### Pole `headless`

Pole `headless` odnosi się do paczek (bundli) liściowych (leaf bundles). Jeśli jest ustawione na `true`, opcje renderowania i listy są ustawione na nigdy, tworząc paczkę bez głównej strony.

- **Definicja**: `headless` jest typem boolean, który ma zastosowanie do paczek liściowych. Gdy jest ustawione na `true`, powoduje to, że opcje renderowania i listowania dla paczki są wyłączone. Oznacza to, że paczka zawiera zasoby strony, ale nie ma pojedynczej głównej strony, którą Hugo normalnie by generowało.

- **Format**: `headless` jest wartością boolean, czyli może przyjąć wartość `true` lub `false`. Domyślnie ustawione na `false`, co oznacza normalne zachowanie generowania stron przez Hugo.

- **Zastosowanie**: Ustawienie `headless` jest przydatne, gdy chcesz grupować zasoby strony bez generowania głównej strony, na przykład do przechowywania zasobów multimedialnych lub innych plików, które nie wymagają oddzielnej strony do wyświetlenia.

- **Przykład**: Jeśli tworzysz galerię obrazów w Hugo, możesz stworzyć paczkę liściową (`leaf bundle`) z ustawionym `headless: true`, aby grupować wszystkie obrazy w jednym miejscu, bez potrzeby generowania oddzielnych stron dla każdego obrazu.

- **Uwaga**: Użycie `headless` jest szczególnie przydatne w przypadku projektów wymagających organizacji i grupowania zasobów, które nie mają potrzeby posiadania tradycyjnej strony do renderowania.

### Pole `isCJKLanguage`

Pole `isCJKLanguage` służy do określenia, czy język zawartości należy do rodziny CJK (chiński, japoński, koreański). Ustawienie tego pola na `true` wpływa na sposób obliczania liczby słów oraz może mieć wpływ na wartości zwracane przez metody takie jak `WordCount`, `FuzzyWordCount`, `ReadingTime`, oraz `Summary` na obiekcie `Page`.

- **Definicja**: `isCJKLanguage` jest typem boolean, który jest używany do oznaczenia języków z rodziny CJK, które mają inne reguły podziału słów i znaków niż języki alfabetyczne. Hugo dostosowuje sposób obliczania takich wartości jak liczba słów i czas czytania w zależności od ustawienia tego pola.

- **Format**: `isCJKLanguage` przyjmuje wartość `true` lub `false`. Domyślnie ustawione na `false`. Języki CJK charakteryzują się specyficznymi wymaganiami co do podziału słów, dlatego Hugo może potrzebować dodatkowych reguł obliczania tych parametrów.

- **Zastosowanie**: Ustawienie `isCJKLanguage` jest istotne dla precyzyjnego obliczania statystyk dotyczących tekstu w językach CJK, takich jak liczba słów, czas czytania, czy krótkie podsumowania. Umożliwia to dokładne dostosowanie wyświetlanych informacji w interfejsie użytkownika.

### Pole `keywords`

Pole `keywords` jest używane do określenia słów kluczowych, które są zazwyczaj wykorzystywane jako meta tagi HTML lub do klasyfikacji treści.

- **Definicja**: `keywords` jest tablicą stringów, która zawiera słowa kluczowe lub frazy, które najlepiej opisują zawartość strony. Te słowa kluczowe mogą być używane do optymalizacji wyszukiwania (SEO) oraz jako etykiety do klasyfikacji treści.

- **Format**: `keywords` jest tablicą stringów, gdzie każdy element reprezentuje pojedyncze słowo kluczowe. Przykładem może być: `keywords: ["Hugo", "static site generator", "web development"]`.

- **Zastosowanie**: Ustawienie `keywords` jest przydatne dla identyfikacji i indeksowania strony przez wyszukiwarki internetowe. Słowa kluczowe pomagają również użytkownikom szybko zrozumieć tematykę i zawartość strony.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartości zawarte w polu `keywords` mogą być odczytywane i wykorzystywane za pomocą metody `Keywords` na obiekcie `Page`. Jest to przydatne do dynamicznego renderowania meta tagów HTML lub do kategoryzacji treści.

- **Przykład**: Jeśli tworzysz stronę o programowaniu w języku Go, możesz użyć `keywords: ["Go programming", "Golang", "web development", "static site generator"]`, aby pomóc wyszukiwarkom internetowym w zrozumieniu, o czym jest Twoja strona.

### Pole `lastmod`

Pole `lastmod` określa datę ostatniej modyfikacji strony. Jest to użyteczne dla śledzenia zmian w treści i aktualizacji stron internetowych.

- **Definicja**: `lastmod` jest typem string, który reprezentuje datę i czas ostatniej modyfikacji strony. Format daty może być różny w zależności od używanego formatu serializacji (JSON, TOML, YAML), ale zazwyczaj jest to `YYYY-MM-DD` lub `YYYY-MM-DDTHH:MM:SSZ`.

- **Zastosowanie**: Ustawienie `lastmod` jest ważne dla optymalizacji wyszukiwania (SEO) oraz dla informowania użytkowników o aktualności zawartości. Wyszukiwarki internetowe mogą użyć tej informacji do określenia, które strony wymagają ponownego zindeksowania.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `lastmod` może być odczytywana i wykorzystywana za pomocą metody `Lastmod` na obiekcie `Page`. Umożliwia to dynamiczne renderowanie informacji o ostatniej modyfikacji na stronie.

- **Przykład**: Jeśli edytujesz stronę regularnie, ustawienie `lastmod` na aktualną datę i godzinę pomoże wskazać wyszukiwarkom, że zawartość strony została zaktualizowana. Przykładem może być `lastmod: "2024-06-19T15:30:00Z"`.

- **Uwaga**: Używanie `lastmod` jest zalecane, aby zapewnić dokładne informacje o aktualności strony. Wpływa to na SEO i może zwiększyć wiarygodność treści w oczach użytkowników.

### Pole `layout`

Pole `layout` pozwala określić nazwę szablonu, który ma zostać użyty do renderowania danej strony. Jest to przydatne do specyfikowania niestandardowych szablonów dla określonych stron w projekcie.

- **Definicja**: `layout` jest stringiem, który reprezentuje nazwę szablonu do użycia dla danej strony. Nazwa ta odpowiada nazwie pliku szablonu bez rozszerzenia pliku. Na przykład, `layout: "post"` odnosi się do pliku `layouts/post.html` lub `layouts/post.<format>`.

- **Zastosowanie**: Ustawienie `layout` pozwala na wybór konkretnego szablonu do renderowania strony, pomimo domyślnego porządku wyszukiwania szablonów w Hugo. Jest przydatne, gdy potrzebujesz niestandardowego układu lub stylu dla określonych rodzajów treści.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `layout` może być odczytywana i wykorzystywana za pomocą metody `Layout` na obiekcie `Page`. Pozwala to na dynamiczne dostosowanie renderowania strony w zależności od określonego szablonu.

- **Przykład**: Jeśli chcesz użyć niestandardowego szablonu dla wpisów na blogu, możesz ustawić `layout: "post"` w front matter danego wpisu. Wtedy Hugo będzie renderować ten wpis używając szablonu `layouts/post.html`.

- **Uwaga**: Używanie `layout` jest przydatne w przypadku projektów wymagających różnych układów dla różnych rodzajów treści. Umożliwia to elastyczność i personalizację wyglądu strony na poziomie indywidualnych wpisów lub stron.

### Pole `linkTitle`

Pole `linkTitle` jest używane do określenia krótszej wersji tytułu strony lub wpisu, która jest zazwyczaj wykorzystywana jako tekst linku.

- **Definicja**: `linkTitle` jest stringiem, który reprezentuje krótszą wersję tytułu strony lub wpisu. Jest to użyteczne, gdy pełny tytuł jest zbyt długi lub gdy potrzebny jest bardziej zwięzły opis w kontekście linków lub nawigacji.

- **Zastosowanie**: Ustawienie `linkTitle` pozwala na użycie bardziej kompaktowej formy tytułu jako tekstu linku w nawigacji lub listach treści. Jest to szczególnie użyteczne w projektach, gdzie istnieje potrzeba zarządzania długimi tytułami w sposób bardziej efektywny.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `linkTitle` może być odczytywana i wykorzystywana za pomocą metody `LinkTitle` na obiekcie `Page`. Umożliwia to dynamiczne renderowanie tekstów linków w zależności od ustawionego `linkTitle`.

- **Przykład**: Jeśli tytuł strony lub wpisu jest długi, na przykład `Long Title of the Blog Post`, możesz ustawić `linkTitle: "Short Title"`, co umożliwi korzystanie z krótszej wersji tytułu jako tekstu linku.

### Pole `markup`

Pole `markup` służy do określenia formatu zawartości, który jest renderowany przez Hugo.

- **Definicja**: `markup` jest stringiem, który identyfikuje format zawartości, takiego jak Markdown, HTML, czy AsciiDoc. Określenie `markup` pozwala Hugo na dokładne ustalenie, jakiego renderera użyć do przetwarzania treści zawartej w pliku.

- **Zastosowanie**: Ustawienie `markup` jest przydatne, gdy nazwa pliku nie jednoznacznie określa format zawartości, albo gdy potrzebny jest niestandardowy render dla określonej treści. Na przykład, jeśli plik ma rozszerzenie `.md`, ale zawiera treść w formacie AsciiDoc, możesz użyć `markup: "asciidoc"`, aby wyraźnie wskazać Hugo, jak renderować tę zawartość.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `markup` może być odczytywana i wykorzystywana za pomocą metody `Markup` na obiekcie `Page`. Umożliwia to dynamiczne dostosowanie renderowania zawartości w zależności od ustawionego formatu `markup`.

### Pole `menus`

Pole `menus` pozwala na dodanie strony do określonych menu.

- **Definicja**: `menus` może przyjmować różne formy danych:
  - String: Nazwa jednego menu, do którego ma zostać dodana strona.
  - String array: Tablica nazw menu, do których ma zostać dodana strona.
  - Map: Mapa, gdzie kluczami są nazwy menu, a wartościami są opcje specyficzne dla menu.

- **Zastosowanie**: Ustawienie `menus` jest przydatne, gdy chcesz zintegrować stronę z nawigacją lub menu na stronie internetowej. Pozwala to na łatwe zarządzanie tym, gdzie i jak strona będzie widoczna w interfejsie użytkownika.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `menus` może być odczytywana i wykorzystywana za pomocą metody `Menus` na obiekcie `Page`. Umożliwia to dynamiczne dodawanie stron do różnych menu w zależności od potrzeb projektowych.

- **Przykład**: Jeśli masz menu główne oraz menu nawigacyjne w stopce strony, możesz ustawić `menus: ["main", "footer"]` w front matter danej strony, aby dodać tę stronę zarówno do menu głównego, jak i do menu w stopce.

### Pole `outputs`

Pole `outputs` pozwala na określenie formatów wyjściowych, które mają zostać wygenerowane dla danej strony.

- **Definicja**: `outputs` jest tablicą stringów, gdzie każdy element reprezentuje format wyjściowy, który ma być wygenerowany dla strony. Formaty te mogą obejmować HTML, JSON, XML i inne formaty wspierane przez Hugo.

- **Zastosowanie**: Ustawienie `outputs` jest przydatne, gdy chcesz, aby Hugo wygenerował różne wersje danej strony w różnych formatach. Na przykład, jeśli tworzysz stronę, która ma być dostępna jako HTML dla przeglądarki internetowej i jako JSON do pobrania danych przez API, możesz ustawić `outputs: ["html", "json"]`.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `outputs` może być odczytywana i wykorzystywana za pomocą metody `Outputs` na obiekcie `Page`. Umożliwia to dynamiczne dostosowanie generowania różnych formatów wyjściowych w zależności od potrzeb.

### Pole `params`

Pole `params` pozwala na definiowanie niestandardowych parametrów strony za pomocą mapy.

- **Definicja**: `params` jest mapą, która zawiera niestandardowe parametry strony, które można dostosować i używać w szablonach Hugo. Parametry te są specyficzne dla danej strony i mogą zawierać różne informacje lub ustawienia potrzebne do renderowania lub funkcjonowania strony.

- **Zastosowanie**: Ustawienie `params` jest przydatne, gdy potrzebujesz przechowywać i używać niestandardowych danych lub ustawień dla danej strony. Może to obejmować konfiguracje specyficzne dla funkcjonalności strony, takie jak klucze API, ustawienia wyświetlania, czy niestandardowe dane potrzebne do renderowania treści.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartości przechowywane w `params` mogą być odczytywane i wykorzystywane za pomocą metody `Param` na obiekcie `Page`. Umożliwia to dynamiczne dostosowanie działania szablonów w zależności od ustawionych parametrów.

- **Przykład**: Jeśli tworzysz stronę, która integruje się z zewnętrznym API i wymaga ustawienia klucza dostępowego, możesz dodać `params` w front matter tej strony, aby przechowywać klucz API i użyć go w szablonach do komunikacji z API.

### Pole `publishDate`

Pole `publishDate` określa datę publikacji strony. Przed tą datą strona nie będzie renderowana, chyba że użyjesz flagi `--buildFuture` w poleceniu Hugo.

- **Definicja**: `publishDate` jest stringiem reprezentującym datę publikacji strony. Jest to przydatne pole, które pozwala na planowanie publikacji treści w Hugo. Strona nie zostanie wygenerowana do pliku wyjściowego przed datą ustawioną w `publishDate`, chyba że zastosowano flagę `--buildFuture`.

- **Zastosowanie**: Ustawienie `publishDate` jest szczególnie użyteczne, gdy chcesz kontrolować moment publikacji treści na stronie internetowej. Możesz planować wydanie nowych artykułów, aktualizacji lub kampanii marketingowych, które mają być widoczne dla użytkowników w określonym czasie.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `publishDate` może być odczytywana i wykorzystywana za pomocą metody `PublishDate` na obiekcie `Page`. Umożliwia to dynamiczne dostosowanie prezentacji strony w zależności od ustawionej daty publikacji.

### Pole `resources`

Pole `resources` umożliwia dostarczenie metadanych dla zasobów strony za pomocą tablicy map.

- **Definicja**: `resources` jest tablicą map, gdzie każdy element mapy zawiera metadane dla konkretnego zasobu strony. Zasoby te mogą obejmować obrazy, pliki audio, video, czy inne pliki, które są powiązane z treścią strony i wymagają dodatkowych informacji lub ustawień.

- **Zastosowanie**: Ustawienie `resources` jest przydatne, gdy potrzebujesz zarządzać dodatkowymi danymi lub ustawieniami dla różnych zasobów na stronie. Może to obejmować metadane techniczne, takie jak wymiary obrazu, format pliku, czy inne szczegóły używane do renderowania i prezentacji zasobów.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, metadane zawarte w `resources` mogą być odczytywane i wykorzystywane za pomocą odpowiednich metod dostępu do zasobów na obiekcie `Page`. Umożliwia to dynamiczne renderowanie zasobów w zależności od ustawionych metadanych.

- **Format**: `resources` jest tablicą map, gdzie każda mapa może zawierać różne pola metadanych, zależnie od potrzeb projektowych. Przykładowe pola mogą obejmować `title`, `description`, `type` (typ zasobu), `params` (niestandardowe parametry) i inne.

- **Przykład**: Jeśli masz stronę zawierającą galerię zdjęć, możesz użyć `resources` w front matter każdego zdjęcia, aby określić tytuł, opis oraz inne szczegóły techniczne takie jak rozmiar i format pliku.

### Pole `sitemap`

Pole `sitemap` umożliwia konfigurację opcji mapy witryny (sitemap) dla danej strony.

- **Definicja**: `sitemap` jest mapą, która zawiera opcje konfiguracyjne dotyczące mapy witryny (sitemap) dla strony. Sitemap jest strukturą XML, która zawiera informacje o strukturze i hierarchii stron na stronie internetowej, co pomaga wyszukiwarkom internetowym w ich indeksowaniu.

- **Zastosowanie**: Ustawienie `sitemap` pozwala na kontrolę, czy i jak strona ma być uwzględniana w mapie witryny generowanej przez Hugo. Możesz określić różne opcje, takie jak `changefreq` (częstotliwość zmian), `priority` (priorytet) i inne parametry pomocne w optymalizacji SEO.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, opcje zawarte w `sitemap` mogą być odczytywane i wykorzystywane za pomocą metody `Sitemap` na obiekcie `Page`. Umożliwia to dynamiczne dostosowanie zawartości mapy witryny w zależności od ustawionych opcji.

- **Format**: `sitemap` jest mapą, gdzie każdy klucz reprezentuje nazwę opcji mapy witryny, a wartość jest odpowiednią wartością tej opcji, na przykład `changefreq: "weekly"`.

- **Przykład**: Jeśli chcesz, aby dana strona była indeksowana częściej przez wyszukiwarki internetowe, możesz ustawić `sitemap: { changefreq: "daily", priority: 0.8 }` w jej front matter. Hugo wykorzysta te informacje do generowania odpowiednich wpisów w mapie witryny.

### Pole `slug`

Pole `slug` w front matter jest używane do nadpisywania ostatniego segmentu ścieżki URL generowanej dla danej strony. Jest to przydatne, gdy chcesz mieć kontrolę nad tym, jak konkretna strona jest adresowana w przeglądarce.

- **Definicja**: `slug` jest ciągiem znaków (stringiem), który zastępuje ostatni segment w ścieżce URL strony. Domyślnie Hugo tworzy ścieżkę URL na podstawie tytułu lub nazwy pliku, ale możesz użyć `slug`, aby to nadpisać.

- **Zastosowanie**: Ustawiając `slug`, możesz zmienić lub uprościć adres URL strony, co jest przydatne zwłaszcza w przypadku stron z długimi tytułami lub gdy chcesz bardziej kontrolować strukturę URL.

- **Przykład**: Jeśli masz stronę z tytułem "Mój pierwszy wpis na blogu", to domyślnie Hugo może utworzyć URL typu `/posts/moj-pierwszy-wpis-na-blogu/`. Możesz jednak ustawić `slug` na `"moj-pierwszy-wpis"`, aby uzyskać bardziej krótki URL, np. `/posts/moj-pierwszy-wpis/`.

- **Uwaga**: Pole `slug` nie jest stosowane dla stron sekcji (np. listy postów), ponieważ Hugo automatycznie zarządza generowaniem ich URLi na podstawie nazwy sekcji i nazw plików wewnątrz sekcji.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `slug` może być uzyskana za pomocą metody `Slug` na obiekcie `Page`. Jest to przydatne do tworzenia dynamicznych linków w szablonach lub do generowania specjalnych odnośników w menu nawigacyjnym.

Pole `slug` daje użytkownikowi kontrolę nad strukturą URL danej strony, co pozwala na bardziej czytelną i optymalizowaną dla SEO adresację stron w Twoim projekcie Hugo.

### Pole `summary`

Pole `summary` służy do dostarczenia krótkiego opisu lub podsumowania zawartości strony. Jest to odrębne koncepcyjnie niż opis strony, ponieważ `summary` ma na celu streszczenie treści lub pełnić rolę teaseru, zachęcając czytelników do odwiedzenia strony.

- **Definicja**: `summary` jest stringiem, który zawiera krótki opis lub streszczenie treści strony. Jest to użyteczne pole, które pomaga w szybkim zrozumieniu tematu strony bez konieczności czytania całej treści.

- **Zastosowanie**: Ustawienie `summary` jest szczególnie przydatne w przypadku list stron, stron głównych, archiwów czy innych miejsc, gdzie istotne jest dostarczenie kompaktowego podsumowania treści. Może ono być również używane jako teaser w różnych kontekstach, takich jak listy wyników wyszukiwania, podgląd postów na blogu, czy w podsumowaniach na stronie głównej.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `summary` może być odczytywana i wykorzystywana za pomocą metody `Summary` na obiekcie `Page`. Pozwala to na dynamiczne wyświetlanie streszczeń w zależności od ustawionych wartości `summary` w front matter strony.

### Pole `title`

Pole `title` w front matter Hugo zawiera tytuł strony.

- **Definicja**: `title` jest stringiem reprezentującym tytuł strony. Jest to kluczowe pole, które określa, jak strona będzie się nazywać w interfejsie użytkownika i w wynikach wyszukiwania.

- **Zastosowanie**: Ustawienie `title` jest niezbędne do określenia nazwy strony. Jest ono używane w różnych kontekstach, takich jak tytuły stron internetowych, nagłówki artykułów, tytuły wpisów na blogu itp. `title` powinno klarownie przedstawiać treść strony i być zwięzłe, ale jednocześnie przyciągające uwagę czytelnika.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `title` jest dostępna za pomocą metody `Title` na obiekcie `Page`. Pozwala to na dynamiczne wyświetlanie tytułów stron na podstawie ustawionych wartości `title` w front matter.

- **Przykład**: Dla strony zawierającej artykuł o najnowszych technologiach, przykładowy `title` mógłby wyglądać tak: `title: "Najnowsze trendy technologiczne roku 2024"`. Taki tytuł jasno określa temat artykułu i przyciąga uwagę czytelników.

- **Uwaga**: Ustawienie odpowiedniego `title` jest kluczowe dla SEO (optymalizacji dla wyszukiwarek internetowych), ponieważ tytuł strony jest jednym z czynników branych pod uwagę przez wyszukiwarki przy indeksowaniu i wyświetlaniu wyników wyszukiwania.

### Pole `translationKey`

Pole `translationKey` jest arbitralną wartością używaną do powiązania dwóch lub więcej tłumaczeń tej samej strony.

- **Definicja**: `translationKey` jest stringiem, który służy do identyfikacji powiązanych tłumaczeń tej samej strony. Jest szczególnie użyteczne, gdy tłumaczenia stron nie mają wspólnego ścieżki URL.

- **Zastosowanie**: Ustawienie `translationKey` pozwala na powiązanie różnych wersji językowych tej samej strony, które mogą znajdować się w różnych katalogach lub nie dzielić wspólnej struktury URL. Jest to przydatne w wielojęzycznych witrynach internetowych, gdzie każda strona może mieć swój unikalny URL w zależności od języka.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `translationKey` jest dostępna za pomocą metody `TranslationKey` na obiekcie `Page`. Umożliwia to dynamiczne odwoływanie się do powiązanych tłumaczeń strony i dostosowanie wyświetlania zawartości w zależności od wybranego języka.

- **Przykład**: Dla strony o nazwie "about" mającej tłumaczenia w języku angielskim i niemieckim, możesz ustawić `translationKey` jako identyfikator, na przykład `translationKey: "about-page"`. Oba tłumaczenia strony będą się odwoływać do tego samego klucza, mimo że ich struktura URL może się różnić.

### Pole `type`

Pole `type` służy do określenia typu zawartości strony, nadpisując wartość domyślną pochodzącą z sekcji na najwyższym poziomie, w której strona się znajduje.

- **Definicja**: `type` jest stringiem, który określa specyficzny typ zawartości strony. Jest używany do klasyfikacji i identyfikacji różnych typów zawartości na stronie internetowej.

- **Zastosowanie**: Ustawienie `type` pozwala na precyzyjne określenie charakteru strony, niezależnie od tego, w jakiej sekcji strona się znajduje. Na przykład, może to być `post` dla wpisu na blogu, `product` dla strony produktu, `event` dla strony wydarzenia itp.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `type` jest dostępna za pomocą metody `Type` na obiekcie `Page`. Umożliwia to dynamiczne przypisanie specyficznego szablonu lub stylizacji w zależności od typu zawartości strony.

- **Przykład**: Dla strony zawierającej opis wydarzenia, możesz ustawić `type` jako `event`, na przykład `type: "event"`. Taka klasyfikacja pozwala na specyficzne przypisanie szablonu wyświetlania dla stron tego typu.

### Pole `url`

Pole `url` umożliwia nadpisanie całej ścieżki URL strony.

- **Definicja**: `url` jest stringiem, który pozwala określić niestandardową ścieżkę URL dla danej strony. Nadpisuje domyślną ścieżkę URL, która byłaby generowana na podstawie hierarchii sekcji i nazwy pliku.

- **Zastosowanie**: Ustawienie `url` jest przydatne, gdy chcesz kontrolować dokładną strukturę URL danej strony. Może być stosowane zarówno do standardowych stron, jak i stron sekcji.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `url` może być odczytywana za pomocą metody `URL` na obiekcie `Page`. Umożliwia to dynamiczne generowanie linków i odwołań do stron, uwzględniając niestandardowe ścieżki URL zdefiniowane w front matter.

- **Przykład**: Jeśli masz stronę o nazwie `about.md` i chcesz, aby jej URL był `/company/about-us/`, możesz ustawić `url: "/company/about-us/"` w jej front matter.

- **Uwaga**: Ustawienie `url` jest opcjonalne. Domyślnie Hugo generuje ścieżki URL na podstawie struktury plików i sekcji. `url` pozwala na niestandardowe definiowanie adresów URL, co jest szczególnie użyteczne w przypadku tworzenia przyjaznych dla użytkownika adresów URL.

### Pole `weight`

Pole `weight` służy do określenia wagi strony, która jest używana do kolejności stron w ramach kolekcji stron.

- **Definicja**: `weight` jest liczbą całkowitą (int), która określa priorytet lub kolejność strony w ramach zbioru stron, takiego jak strony sekcji lub listy stron.

- **Zastosowanie**: Ustawienie `weight` pozwala na manualne określenie, jak strona powinna być ułożona w porównaniu do innych stron w tej samej kolekcji. Niższa wartość `weight` oznacza wyższy priorytet i umieszczenie strony wcześniej w kolekcji.

- **Dostęp z poziomu szablonów**: W szablonach Hugo, wartość `weight` jest dostępna za pomocą metody `Weight` na obiekcie `Page`. Umożliwia to sortowanie i prezentację stron zgodnie z ich określoną wagą.

- **Przykład**: Dla sekcji bloga, gdzie strony są sortowane według daty lub innych kryteriów, możesz ustawić `weight`, aby ręcznie kontrolować kolejność wyświetlania niezależnie od innych kryteriów sortowania.

- **Uwaga**: Ustawienie `weight` jest opcjonalne. Domyślnie strony są zwykle sortowane według daty lub alfabetycznie. Użycie `weight` jest przydatne, gdy potrzebujesz specyficznej kontroli nad kolejnością wyświetlania stron w ramach kolekcji.
