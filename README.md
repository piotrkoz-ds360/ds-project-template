# Tytuł projektu

_Krótki opis: jakie pytanie lub problem rozwiązuje projekt i na jakich danych._

## Struktura repozytorium

```
├── .github/
│   └── pull_request_template.md   szablon opisu pull requesta
├── data/                          dane (poza Gitem, opis w data/README.md)
│   ├── raw/                       dane źródłowe, nigdy nie edytowane
│   └── processed/                 dane po przetworzeniu
├── docs/                          dokumentacja i decyzje projektowe
├── notebooks/                     notatniki Jupyter (eksploracja, analizy)
├── src/                           kod wielokrotnego użytku (moduły .py)
├── .env.example                   wzór pliku ze zmiennymi środowiskowymi
├── .gitattributes                 normalizacja końców linii
├── .gitignore                     pliki wyłączone z repozytorium
├── CONTRIBUTING.md                zasady pracy z repozytorium
└── requirements.txt               zależności
```

## Uruchomienie

Wymagany Python 3.13. Polecenia dla PowerShella na Windowsie;
na macOS/Linuksie zamiast `.venv\Scripts\` używa się `.venv/bin/`.

**pip**

```
py -3.13 -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

**uv**

```
uv venv --python 3.13
uv pip install -r requirements.txt
```

Zmienne środowiskowe (np. klucze API) należy skopiować z `.env.example`
do pliku `.env` i uzupełnić.

## Dane

Dane nie są przechowywane w repozytorium. Źródła i sposób pobrania
opisuje [data/README.md](data/README.md).

## Wyniki

_Do uzupełnienia: najważniejsze wnioski i miejsce, w którym można je znaleźć
(notatnik, raport w `docs/`)._
