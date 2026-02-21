# income-prediction-regression
## Opis projektu
Projekt analityczny badający przewidywanie dochodu za pomocą regresji liniowej. Kluczowym elementem jest detekcja oraz usunięcie wartości odstających metodą IQR, a także bezpośrednie porównanie skuteczności modeli na danych surowych i oczyszczonych.

## Zbiór danych
Projekt wykorzystuje plik `data.csv`, który zawiera szczegółowe informacje dotyczące 20 000 osób z Indii. 
* **Zmienna objaśniana (Target):** `Income` (Miesięczny dochód).
* **Zmienne objaśniające (Features):** Dane demograficzne (np. `Age`, `Education`, `Sector`, `City_Tier`) oraz finansowe (m.in. `Rent`, `Groceries`, `Transport`, `Healthcare`, `Savings_Goal`).

## Etapy analizy i modelowania
1. **Wczytanie i eksploracja danych**: Zrozumienie rozkładu zmiennych, identyfikacja braków danych oraz wstępna analiza zależności.
2. **Budowa Modelu 1**: Wytrenowanie pierwszego modelu regresji liniowej na danych zawierających wartości odstające.
3. **Detekcja i obsługa wartości odstających**: Wykorzystanie metody rozstępu międzykwartylowego (**IQR - Interquartile Range**) do zidentyfikowania i usunięcia skrajnych wartości, które mogłyby zaburzyć działanie algorytmu.
4. **Budowa Modelu 2**: Ponowne wytrenowanie modelu na poprawionym zbiorze danych.
5. **Ewaluacja i porównanie**: Zestawienie wyników obu modeli przy użyciu metryk takich jak błąd średniokwadratowy (**RMSE**) oraz współczynnik determinacji (**R²**).

## Główne wnioski
Projekt dobitnie pokazuje, jak wrażliwa jest regresja liniowa na wartości odstające. Porównanie modeli dało następujące rezultaty:

* **Model 1 (z wartościami odstającymi):** * Wyniki były bardzo słabe: **RMSE = ~18 601.87**, a **R² = 0.39** (model wyjaśniał zaledwie 39% zmienności). 
  * *Wniosek:* Algorytm na siłę próbował dopasować linię trendu do skrajnych obserwacji (np. osób o gigantycznych dochodach), przez co tracił precyzję dla standardowych przypadków.
* **Model 2 (po usunięciu wartości odstających metodą IQR):** * Wyniki uległy drastycznej poprawie: **RMSE = ~4 561.58** (błąd spadł ponad czterokrotnie!), a **R² = 0.87**.
  * *Wniosek:* Oczyszczenie danych pozwoliło modelowi skupić się na głównym, reprezentatywnym wzorcu, co zaowocowało dopasowaniem na poziomie 87%.

## Technologie i Biblioteki
Projekt został w całości przygotowany w języku Python. Główne wykorzystane pakiety to:
* `pandas`, `numpy` – do manipulacji, przekształceń i inżynierii danych,
* `matplotlib`, `seaborn` – do tworzenia wykresów i eksploracji wizualnej,
* `scikit-learn` – do preprocessingu, trenowania modeli predykcyjnych i ich ewaluacji.

## Jak uruchomić projekt
1. Sklonuj repozytorium na swój dysk.
2. Upewnij się, że masz zainstalowane środowisko Python z pakietami wymienionymi wyżej.
3. Projekt był tworzony z myślą o środowisku Google Colab. Jeśli chcesz go tam uruchomić, wywołaj pierwszą komórkę z google.colab.files.upload() i wgraj pliki .csv.
4. Aby uruchomić go lokalnie, wystarczy umieścić plik `data.csv` w jednym folderze z notatnikiem i pominąć komórkę odpowiedzialną za upload.
5. Uruchamiaj kolejne komórki kodu.

