# Oceny okresowe - Bartosz Kozłowski

Domena cyklicznych ocen okresowych analityków, które wystawiam (kilka w roku, ten sam formularz). Agent zbiera dowody i przygotowuje szkic karty; ocenę wystawiam ja i przenoszę ją do systemu ocen.

## Struktura

- `szablon/karta-oceny-analityka.md` - struktura formularza (źródło: pusta karta z 2026-03, wersja PDF v1). Zmiana formularza w firmie = nowa wersja szablonu z datą w nagłówku, stare oceny zostają na starej wersji.
- `oceny/<rrrr-mm>-<inicjały>/` - jedna ocena:
  - `stan-pracy.md` - etap, co zostało, termin;
  - `kontekst.md` - kogo oceniam, rola, projekt, okres oceny, data przyjścia, login w Bitbucket;
  - `dowody.md` - fakty z odnośnikami (PR, komentarz, data), bez ocen;
  - `karta.md` - kopia szablonu wypełniona na podstawie `dowody.md`.

## Przebieg oceny

1. Załóż katalog oceny, skopiuj szablon do `karta.md`, uzupełnij `kontekst.md` (o brakujące dane zapytaj mnie).
2. Zbierz dowody do `dowody.md`, pisząc plik sekcja po sekcji w trakcie pracy:
   - pull requesty, commity i komentarze z review osoby w okresie oceny (Bitbucket, token tylko do odczytu, zob. pamięć agenta);
   - moje notatki i obserwacje, które podam w sesji.
3. Wypełnij `karta.md`: przy każdym zaznaczonym punkcie odnośnik do dowodu; punkt bez dowodu oznacz jako "do potwierdzenia przez Bartosza", nie zaznaczaj go.
4. Tabela "Feedback" i "Skrócona opinia" to szkic do mojej redakcji: konkretne przykłady, cele mierzalne.
5. Wpisz pytania do mnie na końcu `stan-pracy.md` jako listę numerowaną, z rekomendowaną odpowiedzią.
6. Kartę na wiki przenoszę ja, ręcznie. Agent na wiki nic nie wpisuje; przygotowuje `karta.html` do przeklejenia (zob. "Doświadczenia z ocen").
7. Po moim przeniesieniu: porównaj stronę wiki z `karta.md`, wynik w `porownanie-wiki.md` w katalogu oceny. Oryginałem oceny jest wiki; `karta.md` nie synchronizuj.

## Zasady

- Oceniam pracę na podstawie faktów. Nie wyciągaj wniosków o osobie z braku danych; brak dowodu to pytanie do mnie.
- Dane osobowe ocenianych i treść ocen nie wychodzą poza `oceny/` tego repozytorium: nie trafiają na tablicę koordynacji, do innych repozytoriów, plików przeglądów w `~/.cache/ai-agents/review/` ani do zewnętrznych usług (Slack, Docs, Artifact).
- Materiał zastrzeżony Prostej Hipoteki (zob. `GIT/eximee-alior-hipo`, ADR-0006): Claude go nie czyta. Gdy ocena wymaga jego treści, sesja Qwen pisze podsumowanie bez materiału zastrzeżonego, a ono trafia do `dowody.md`.
- Wcześniejsze oceny: indeks w `oceny/archiwum.md`, treść w ich katalogach. Oryginały to strony wiki Consdaty (intranet, strona "<rrrr-mm> Kozłowski Bartosz ocenia <osoba>" pod stroną osoby w jej Chapterze); wiki czytaj tokenem z pamięci agenta. Przed nową oceną przeczytaj archiwum: styl, poziom szczegółu i poprzednie cele tej samej osoby.
- Ostatnia karta osoby: sprawdź, czy cele krótkoterminowe z niej zostały osiągnięte, i napisz to w `dowody.md`.

## Mój styl ocen (z wcześniejszych kart)

- Ciężar oceny w tabeli Feedback; kratki i Wartości bywają niewypełnione, więc pytaj, czy tym razem je wypełniamy.
- Po jednym konkretnym celu krótkoterminowym i długoterminowym, związanym z systemem, w którym osoba pracuje.
- "Co poszło dobrze" z konkretnymi przykładami (narzędzia, inicjatywy), "Co poprawić" sformułowane jako naturalny następny krok.
- Skrócona opinia ciepła i bezpośrednia, kontekst stażu, na końcu jednozdaniowa rekomendacja wprost (np. dalsza współpraca, droga do poziomu Regular).
- Tablica koordynacji dostaje tylko wiersz "Ocena okresowa" z terminem, bez nazwiska.

## Doświadczenia z ocen

Wnioski z poprzednich sesji (ocena 2026-11, koniec okresu próbnego).

Na starcie:
- Zaszeregowanie sprawdź na wiki, zanim przyjmiesz poziom: strona "Stanowiska - zestawienie" (pageId 143327645), kolumna "Zaszeregowanie". R1 to pierwszy stopień Regulara (moje wyjaśnienie). Raz przyjęty z rozmowy poziom okazał się nieaktualny.
- Ustal cel oceny: ocena okresowa czy koniec okresu próbnego. Przy okresie próbnym na podstawie tej i innych ocen PO prowadzi rozmowę i decyduje o dalszej współpracy, więc skrócona opinia kończy się rekomendacją w tej sprawie.
- Strona oceny na wiki bywa założona przez kadry wcześniej, jako pusty formularz pod stroną osoby w Chapterze; jej tytuł może mieć odwróconą kolejność nazwisk. Znajdziesz ją wyszukiwaniem CQL po nazwisku osoby.

Źródła dowodów:
- Wklejony czat ze Slacka: nie ma dat dziennych; zapisz kolejność, daty oznacz "do potwierdzenia". Nie przepisuj numerów telefonów, danych testowych, treści komunikatów ani stron banku; imiona osób z banku zamieniaj na role w tekstach, które idą na wiki.
- Historia wersji stron wiki (`/rest/experimental/content/<id>/version`, wersje historyczne `?status=historical&version=<n>`) pokazuje, kto co dopisał. Dobry dowód wkładu we wspólny materiał.
- Poziom samodzielności przypisany przez agenta to propozycja do mojego potwierdzenia.
- Nie przesądzaj autorstwa (np. skryptów), którego nie potwierdziłem; opisz, co osoba robi.

Interpretacja:
- Prośba o wsparcie w dobrym momencie (np. dołączenie mnie do spotkania) to plus, nie słabość.
- Pojedyncza pomyłka poprawiona od razu i niepowtórzona nie jest podstawą do "Co poprawić".
- Gdy w dowodach nie ma przykładu do poprawy, zaproponuj "Co poprawić" jako następny krok w stronę wyższego poziomu, zaczepiony w konkretnym zdarzeniu; podaj 2-3 warianty, wybieram ja.
- Nie przesądzaj, kto przedstawi wyniki pracy na zewnątrz (np. bankowi), jeśli tego nie wiem; pisz tylko, co osoba wykonała.

Wynik do przeniesienia:
- `karta.html` w katalogu oceny: przy każdym punkcie zaznacz / na szaro / puste, przy każdym komentarzu i komórce Wartości i Feedback przycisk "Kopiuj". Tekst do kopiowania bez odnośników `[D..]`; uwagi "do potwierdzenia przez Bartosza" widoczne, ale oznaczone jako niewklejane. Skrypt generujący trzymaj poza katalogiem oceny (scratchpad).
- W `karta.md` rozdziel w każdej sekcji "Komentarz:" (idzie na wiki) i "Do potwierdzenia przez Bartosza:" (zostaje lokalnie).
- Na wiki zaznaczam punkty szerzej niż dowody w `dowody.md` i nie używam szarego. Przy porównaniu sprawdź spójność: komentarz z wzmianką "na szaro" przy punkcie niezaznaczonym, punkt zaznaczony jako spełniony, a jednocześnie będący celem lub "Co poprawić".

## Synchronizacja

- Remote: prywatne konto GitHub `bartekk80-hash`, repozytorium prywatne.
- `.gitignore` wyklucza `oceny/`: do zdalnego repozytorium idą tylko reguły i szablon. Zmiana tego wymaga mojej decyzji.
- Commit i push tylko na moją prośbę; push wymaga mojego logowania, więc podajesz mi komendę.
