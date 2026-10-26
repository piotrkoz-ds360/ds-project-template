# Zasady pracy z repozytorium

## Gałęzie

- `main`: stabilna wersja, aktualizowana fast-forwardem z `develop`
  na zamknięcie etapu prac.
- `develop`: bieżąca praca, gałąź domyślna. Zmiany trafiają tu wyłącznie
  przez pull request.
- Gałęzie robocze tworzy się z aktualnego `develop`, jedna gałąź na jedno zadanie:

| Typ | Kiedy | Przykład |
| --- | --- | --- |
| `feature/` | nowa analiza, notatnik, funkcja | `feature/12-sales-eda` |
| `fix/` | poprawka błędu | `fix/15-missing-dates-in-import` |
| `docs/` | dokumentacja | `docs/3-setup-instructions` |
| `experiment/` | próba, z założenia nie jest łączona | `experiment/18-random-forest` |

Nazwa: `typ/nr-issue-krotki-opis`, małe litery, bez polskich znaków
i spacji, słowa łączone myślnikiem.

Nie pushuje się bezpośrednio do `develop` ani `main`.

## Commity

Uproszczona konwencja [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/):
`typ: opis`. Opis po angielsku, w trybie rozkazującym, małą literą
i bez kropki na końcu (`add`, nie `added` ani `adds`).

| Typ | Kiedy | Przykład |
| --- | --- | --- |
| `feat` | nowa funkcjonalność lub analiza | `feat: add monthly sales plot` |
| `fix` | poprawka błędu | `fix: correct date parsing in data import` |
| `docs` | dokumentacja | `docs: describe data source` |
| `refactor` | zmiana kodu bez zmiany działania | `refactor: move data cleaning to src` |
| `test` | testy | `test: add tests for cleaning function` |
| `chore` | porządki, konfiguracja, zależności | `chore: add scikit-learn to requirements` |

## Pull requesty

- Każda zmiana trafia do `develop` przez pull request z wypełnionym szablonem.
- Opis zawiera `Closes #nr`, żeby issue zamknęło się po połączeniu.
- PR łączy osoba recenzująca, metodą *Rebase and merge*.
- Przed otwarciem PR-a: Restart → Run All w notatnikach, uporządkowane
  commity, gałąź aktualna względem `develop`.
- Po połączeniu:

  ```
  git switch develop
  git pull --prune
  git branch -D typ/nr-issue-krotki-opis
  ```

  `-D` jest potrzebne, bo *Rebase and merge* tworzy na `develop` kopie
  commitów z nowymi identyfikatorami i Git nie rozpoznaje gałęzi jako
  połączonej. Należy go użyć dopiero po sprawdzeniu, że PR jest połączony.

## Rebase

- Rebase wykonuje się tylko na własnej gałęzi roboczej, nigdy na `develop` ani `main`.
- Aktualizacja gałęzi względem `develop`:

  ```
  git fetch
  git rebase origin/develop
  ```

- Po rebase zmiany wypycha się przez `git push --force-with-lease`,
  nigdy przez `git push --force`.

## Notatniki

- Notatnik służy do eksploracji. Kod używany w więcej niż jednym miejscu
  trafia do modułów w `src/`.
- Przed commitem: Restart → Run All. Notatnik musi przejść od początku
  do końca na świeżym kernelu.
- Nazewnictwo i szczegóły: [notebooks/README.md](notebooks/README.md).

## Pliki poza repozytorium

Dane, środowiska wirtualne, plik `.env` i ustawienia IDE są wyłączone
w `.gitignore`. Plik, który trafił do repozytorium przed dodaniem do
`.gitignore`, usuwa się poleceniem `git rm --cached <ścieżka>` i commitem.
Sekret (hasło, klucz API), który trafił do repozytorium, należy uznać
za ujawniony i wymienić, bo zostaje w historii.
