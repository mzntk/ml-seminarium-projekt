# Uczenie maszynowe w Pythonie — referat seminaryjny

Projekt dotyczący uczenia maszynowego, przygotowany na seminarium licencjackie: prezentacja oraz zadania z kodem w Pythonie (scikit-learn).

| | |
|---|---|
| **Kierunek** | Modelowanie matematyczne i analiza danych, semestr 5 |
| **Rok akademicki** | 2026/27 |
| **Seminarium** | Zaawansowana analiza i eksploracja danych |
| **Prowadzący** | dr Adrian Karpowicz |
| **Jednostka** | Wydział Matematyki, Fizyki i Informatyki Uniwersytetu Gdańskiego |
| **Autorzy** | Grzegorz Dudkiewicz, Piotr Orzeł, Maja Zontek |

## Zakres materiału

1. **Wprowadzenie**: uczenie maszynowe a modelowanie statystyczne; uczenie nadzorowane i nienadzorowane
2. **Pojęcia podstawowe**: podział train/test, walidacja krzyżowa (k-fold, leave-one-out), ekstrakcja cech, redukcja wymiaru (PCA)
3. **Regresja**: przeuczenie, regularyzacja (Ridge, LASSO, Elastic Net), dobór parametru α przez walidację krzyżową
4. **Klasyfikacja**: regresja logistyczna, drzewa decyzyjne, k-NN, SVM, Random Forest; metryki (macierz pomyłek, precision, recall, F1)
5. **Klasteryzacja**: K-means, mean-shift, ocena zgodności klastrów z etykietami
6. **Etyka danych**: przypadek zbioru Boston Housing, zmienne proxy, fairness

## Struktura repozytorium

```
.
├── prezentacja/        # slajdy (PDF + źródła)
├── notebooki/          # przykłady z prezentacji (Jupyter)
├── zadania/            # zadania dla studentów
├── dane/               # dodatkowe zbiory danych (jeśli nie są pobierane z kodu)
├── requirements.txt
└── README.md
```

## Materiały do pobrania

Prezentacja i kody (notebooki z przykładami oraz zadania) są dostępne do pobrania na Google Drive:
**[📁 Materiały na Google Drive](https://drive.google.com/drive/u/0/folders/1w3d0p_gCD49CM_WHfohcnO7SVVemomAq)**

Te same pliki znajdują się w repozytorium, w katalogach [`prezentacja/`](prezentacja/), [`notebooki/`](notebooki/) i [`zadania/`](zadania/).

## Uruchomienie

Wymagany Python 3.10+.

**pip:**
```bash
git clone https://github.com/mzntk/ml-seminarium-projekt.git
cd ml-seminarium-projekt
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

**conda:**
```bash
git clone https://github.com/mzntk/ml-seminarium-projekt.git
cd ml-seminarium-projekt
conda create -n ml-seminarium python=3.12
conda activate ml-seminarium
pip install -r requirements.txt
jupyter lab
```

**Google Colab:** `File → Open notebook → GitHub`, wpisz `mzntk/ml-seminarium-projekt` i wybierz notebook. Brakujące pakiety doinstaluj przez `!pip install ...`.

### `requirements.txt`
```
numpy
pandas
matplotlib
seaborn
scikit-learn>=1.4
jupyterlab
```

## Zbiory danych

| Zbiór | Zadanie | Źródło |
|---|---|---|
| Iris | klasyfikacja, klasteryzacja | `sklearn.datasets.load_iris` |
| California Housing | regresja | `sklearn.datasets.fetch_california_housing` (wymaga internetu przy pierwszym uruchomieniu) |
| dane syntetyczne | regresja z regularyzacją | `sklearn.datasets.make_regression` |

Zbiór Boston Housing (`load_boston`) został usunięty ze scikit-learn w wersji 1.2 z powodów etycznych i nie jest używany w projekcie. Jego historię omawiamy w części prezentacji poświęconej etyce danych.

## Źródła

- R. Johansson, *Numerical Python: Scientific Computing and Data Science Applications with Numpy, SciPy and Matplotlib*, wyd. 2, Apress, 2019, rozdz. 15
- T. Hastie, R. Tibshirani, J. Friedman, *The Elements of Statistical Learning*, Springer
- [Dokumentacja scikit-learn](https://scikit-learn.org/stable/)

Kod przykładów z książki Johanssona dostosowaliśmy do aktualnej wersji scikit-learn (1.x): usunięte parametry, nowe wartości domyślne, zamiana zbioru Boston na California Housing.
