# Uczenie maszynowe w Pythonie — referat seminaryjny

Projekt dotyczący uczenia maszynowego, przygotowany na seminarium licencjackie. Składa się z dwóch części:

1. **Teoria**: prezentacja oparta na rozdziale 15 książki R. Johanssona *Numerical Python*.
2. **Ćwiczenia z modelowania**: zbiór `viral_songs.csv`, regresja liczby odtworzeń, klasyfikacja viralowości i klasyfikacja gatunku muzycznego.

| | |
|---|---|
| **Kierunek** | Modelowanie matematyczne i analiza danych, semestr 5 |
| **Rok akademicki** | 2026/27 |
| **Seminarium** | Zaawansowana analiza i eksploracja danych |
| **Prowadzący** | dr Adrian Karpowicz |
| **Jednostka** | Wydział Matematyki, Fizyki i Informatyki Uniwersytetu Gdańskiego |
| **Autorzy** | Grzegorz Dudkiewicz, Piotr Orzeł, Maja Zontek |

## Część teoretyczna

Na podstawie: R. Johansson, *Numerical Python*, wyd. 2, Apress 2019, rozdz. 15 *Machine Learning*.

1. Uczenie maszynowe a modelowanie statystyczne
2. Uczenie nadzorowane i nienadzorowane
3. Walidacja krzyżowa (podział train/test, k-fold, leave-one-out)
4. Ekstrakcja cech, redukcja wymiaru (PCA)
5. Regresja: przeuczenie, regularyzacja (Ridge, LASSO, Elastic Net), dobór α
6. Klasyfikacja: regresja logistyczna, drzewa decyzyjne, k-NN, SVM, Random Forest; metryki
7. Klasteryzacja: K-means, mean-shift

## Część praktyczna: ćwiczenia z modelowania


### Zbiór danych: `viral_songs.csv`

Syntetyczny zbiór 10 000 utworów z lat 2010–2025, opisanych cechami audio w stylu Spotify. Rozkłady cech zależą od gatunku i są wzorowane na opublikowanych statystykach Spotify. Licencja: CC0 (domena publiczna).

| Kolumna | Opis |
|---|---|
| `track_id` | unikalny identyfikator utworu |
| `track_name` | syntetyczna nazwa utworu |
| `artist` | syntetyczna nazwa wykonawcy |
| `genre` | główny gatunek (10 klas: Rock, Hip-Hop, Latin, Pop, Indie, Electronic, Classical, Jazz, R&B, Country) |
| `release_year` | rok wydania (2010–2025) |
| `duration_sec` | długość utworu w sekundach |
| `danceability` | wynik 0–1: na ile utwór nadaje się do tańca |
| `energy` | wynik 0–1: intensywność i aktywność |
| `valence` | wynik 0–1: pozytywny nastrój utworu |
| `tempo_bpm` | tempo w uderzeniach na minutę (BPM) |
| `acousticness` | wynik 0–1: pewność, że utwór jest akustyczny |
| `instrumentalness` | wynik 0–1: przewidywany brak wokalu |
| `speechiness` | wynik 0–1: obecność słów mówionych |
| `liveness` | wynik 0–1: obecność publiczności (nagranie na żywo) |
| `loudness_db` | ogólna głośność w dB |
| `streams` | łączna liczba odtworzeń |
| `viral` | 1, jeśli utwór stał się viralem, 0 w przeciwnym razie |

### Modele

| # | Zadanie | Zmienna celu | Pytanie badawcze |
|---|---|---|---|
| 1 | Regresja | `streams` | Jakie cechy utworu wpływają na liczbę odtworzeń? |
| 2 | Klasyfikacja binarna | `viral` | Czy da się przewidzieć, że utwór stanie się viralem? |
| 3 | Klasyfikacja wieloklasowa | `genre` | Czy gatunki muzyczne mają charakterystyczne cechy audio? |

### Przebieg ćwiczeń

1. Eksploracyjna analiza danych
2. Przygotowanie cech
3. Trenowanie i porównanie modeli:
   - regresja: `LinearRegression`, `Ridge`, `Lasso`, `RandomForestRegressor`
   - klasyfikacja: `LogisticRegression`, `DecisionTreeClassifier`, `KNeighborsClassifier`, `SVC`, `RandomForestClassifier`
4. Ewaluacja na zbiorze testowym
5. Interpretacja wyników i wnioski

## Struktura repozytorium

```
.
├── prezentacja/                     # slajdy (PDF + źródła)
├── dane/
│   └── viral_songs.csv
├── gotowe-notebooki/
│   ├── 00_eda.ipynb                 # eksploracyjna analiza danych
│   ├── 01_regresja_streams.ipynb    # model 1
│   ├── 02_klasyfikacja_viral.ipynb  # model 2
│   └── 03_klasyfikacja_genre.ipynb  # model 3
├── requirements.txt
├── README.md
└── zadania/
    ├── 00_eda_zadanie.ipynb                 # eksploracyjna analiza danych
    ├── 01_regresja_streams_zadanie.ipynb    # model 1
    ├── 02_klasyfikacja_viral_zadanie.ipynb  # model 2
    └── 03_klasyfikacja_genre_zadanie.ipynb  # model 3
```

## Materiały do pobrania

Prezentacja i kody są dostępne do pobrania na Google Drive:
**[📁 Materiały na Google Drive](https://drive.google.com/drive/u/0/folders/1w3d0p_gCD49CM_WHfohcnO7SVVemomAq)**

Te same pliki znajdują się w repozytorium, w katalogach [`prezentacja/`](prezentacja/), [`dane/`](dane/) i [`notebooki/`](notebooki/).

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

**Google Colab:** `File → Open notebook → GitHub`, wpisz `mzntk/ml-seminarium-projekt` i wybierz notebook. Dane można wczytać bezpośrednio z repozytorium:

```python
import pandas as pd
url = "https://raw.githubusercontent.com/mzntk/ml-seminarium-projekt/main/dane/viral_songs.csv"
df = pd.read_csv(url)
```

### `requirements.txt`
```
numpy
pandas
matplotlib
seaborn
scikit-learn>=1.4
jupyterlab
```

## Źródła

- R. Johansson, *Numerical Python: Scientific Computing and Data Science Applications with Numpy, SciPy and Matplotlib*, wyd. 2, Apress, 2019, rozdz. 15
- T. Hastie, R. Tibshirani, J. Friedman, *The Elements of Statistical Learning*, Springer
- [Dokumentacja scikit-learn](https://scikit-learn.org/stable/)
