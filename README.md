# Model Pipeline dla klasyfikacji SPAM/NON-SPAM

## Wprowadzenie

Celem tego projektu jest klasyfikacja wiadomości e-mail jako SPAM lub NON-SPAM przy użyciu modelu **Random Forest**. Wykorzystujemy techniki **przetwarzania języka naturalnego (NLP)**, takie jak czyszczenie tekstu, tokenizacja, usuwanie stopwords, lematyzacja oraz wektoryzacja przy użyciu **CountVectorizer** i **TfidfVectorizer**.

Dodatkowo, wykonujemy **selekcję cech** na podstawie ich istotności (**Feature Importance**) oraz **optymalizujemy hiperparametry** modelu za pomocą **GridSearchCV**.

## Funkcjonalności

### 1. Wczytanie i eksploracja danych:
   - Wczytanie danych z pliku `spam.csv`.
   - Zamiana etykiet (`ham` -> `0`, `spam` -> `1`).
   - Sprawdzenie rozkładu klas oraz podstawowych statystyk tekstu.

### 2. Przetwarzanie tekstu (NLP):
   - **Czyszczenie tekstu**: usunięcie interpunkcji.
   - **Tokenizacja**: podział tekstu na pojedyncze słowa.
   - **Usunięcie stopwords**: eliminacja często występujących, ale mało znaczących słów.
   - **Lematyzacja**: sprowadzenie słów do ich podstawowej formy.

### 3. Wektoryzacja tekstu:
   - **CountVectorizer** (macierz częstości występowania słów).
   - **TfidfVectorizer** (ważona częstość słów - TF-IDF).
   - **Filtrowanie słów** (min_df=0.01, max_df=0.5), aby usunąć rzadkie i zbyt częste słowa.

### 4. Podział zbioru na treningowy i testowy:
   - **80% danych jako treningowe, 20% jako testowe**.
   - **Stratyfikacja**, aby zachować proporcje klas.

### 5. Budowa modelu klasyfikacyjnego:
   - **Random Forest Classifier** (n_estimators=100, random_state=42).
   - Wyciągnięcie **Feature Importance** z modelu.
   - Selekcja cech: zachowanie tylko tych, których ważność jest większa niż **0.001**.

### 6. Optymalizacja hiperparametrów:
   - **GridSearchCV** do znalezienia najlepszych wartości `max_depth`, `n_estimators` i `min_samples_split`.

### 7. Ocena modelu:
   - **Dokładność (accuracy)** przed i po selekcji cech.
   - **Wpływ hiperparametrów na wynik końcowy**.


## Technologie

Projekt został stworzony z użyciem:
- **Python**: Język programowania do analizy danych i uczenia modeli.
- **NLTK**: Przetwarzanie języka naturalnego.
- **Scikit-learn**: Algorytmy uczenia maszynowego, GridSearch, wektoryzacja tekstu.
- **Pandas**: Manipulacja danymi.
- **NumPy**: Operacje na macierzach.
- **Matplotlib/Seaborn**: Wizualizacja danych.

## Pliki projektu:
- `spam.csv`: Zbiór danych e-maili (SPAM/NON-SPAM).
- `NLP.py`: Skrypt implementujący cały proces NLP i klasyfikacji.
- `README.md`: Opis projektu i uzyskanych wyników.

## Uruchomienie projektu
1. **Zainstaluj wymagane biblioteki**:
   ```bash
   pip install numpy pandas scikit-learn nltk matplotlib seaborn
   ```
2. **Uruchom główny skrypt**:
   ```bash
   python NLP.py
   ```
3. **Otrzymasz wyniki dokładności modelu oraz najważniejsze cechy tekstu.**


