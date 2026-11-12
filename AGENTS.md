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

## Zasady

- Oceniam pracę na podstawie faktów. Nie wyciągaj wniosków o osobie z braku danych; brak dowodu to pytanie do mnie.
- Dane osobowe ocenianych i treść ocen nie wychodzą poza `oceny/` tego repozytorium: nie trafiają na tablicę koordynacji, do innych repozytoriów, plików przeglądów w `~/.cache/ai-agents/review/` ani do zewnętrznych usług (Slack, Docs, Artifact).
- Materiał zastrzeżony Prostej Hipoteki (zob. `GIT/eximee-alior-hipo`, ADR-0006): Claude go nie czyta. Gdy ocena wymaga jego treści, sesja Qwen pisze podsumowanie bez materiału zastrzeżonego, a ono trafia do `dowody.md`.
- Wcześniejsze karty (PDF) leżą w `~/Pobrane`. Czytaj je tylko na moją prośbę, np. by porównać postęp osoby.
- Tablica koordynacji dostaje tylko wiersz "Ocena okresowa" z terminem, bez nazwiska.

## Synchronizacja

- Remote: prywatne konto GitHub `bartekk80-hash`, repozytorium prywatne.
- `.gitignore` wyklucza `oceny/`: do zdalnego repozytorium idą tylko reguły i szablon. Zmiana tego wymaga mojej decyzji.
- Commit i push tylko na moją prośbę; push wymaga mojego logowania, więc podajesz mi komendę.
