# Notatniki

Notatniki służą do eksploracji i analiz. Kod używany w więcej niż
jednym miejscu trafia do modułów w `src/`.

## Nazewnictwo

`NN-krotki-opis.ipynb`: dwucyfrowy numer porządkowy, małe litery,
bez polskich znaków i spacji, słowa łączone myślnikiem.

Przykłady: `00-srodowisko.ipynb`, `01-eda-dane-sprzedazowe.ipynb`,
`02-czyszczenie-danych.ipynb`.

## Zasady

- Przed commitem: Restart → Run All. Notatnik musi przejść od początku
  do końca na świeżym kernelu.
- Pierwsza komórka sprawdza środowisko:

```python
import sys
print(sys.version)      # 3.13...
print(sys.executable)   # ...\.venv\Scripts\python.exe
```

- Import własnego kodu z `src/`:

```python
import sys
from pathlib import Path

sys.path.append(str(Path.cwd().parent))  # katalog główny repozytorium

%load_ext autoreload
%autoreload 2     # zmiany w src/ widoczne bez restartu kernela

from src import ...
```
