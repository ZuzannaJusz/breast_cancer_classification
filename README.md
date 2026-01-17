# **Projekt zaliczeniowy – Zastosowania Uczenia Maszynowego**

## **1. Informacje ogólne**
**Nazwa projektu:**  
*Detekcja raka piersi*  

**Autor:**  
Zuzanna Juszczak  

**Kierunek, rok i tryb studiów:**  
*Informatyka, semestr III, studia internetowe*  

**Data oddania projektu:**  
17.01.2026 

---

## **2. Opis projektu**
**Celem projektu jest sklasyfikowanie obrazów mammograficznych jako obrazy przedstawiające guzy łagodne lub złośliwe, wykorzystując trzy różne podejścia. Pierwszym podejściem jest klasyczny algorytm uczenia maszynowego oparty na ekstrakcji cech z obrazów. Wykorzystano PCA, radiomics oraz mix obu podejść, następnie trenowano dane przy użyciu Random Forest. Drugim podejściem jest zaimplementowanie sieci CNN. Trzecie podejście obejmuje model ViT aby wykorzystać nowe techniki głębokiego uczenia i sprawdzić czy osiągają wyższą dokładność.**

---

## **3. Dane**
**Źródło danych:**  
*Kaggle*  

**Link do danych:**  
https://www.kaggle.com/datasets/hayder17/breast-cancer-detection/data

**Opis danych:**  
- liczba próbek:  3383
- format danych:  obraz mammograficzny
- rodzaj etykiet / klas:  0 - benign, 1 - malignant
- licencja:  https://opendatacommons.org/licenses/dbcl/1-0/

**Uwagi:**  
Dane zostały przeprocesowane do odpowiednich formatów względem każdego z algorytmów. Dla Random Forest dane przeszły redukcję wymiarowości, dla CNN oraz ViT zostały zmienione wielkości obrazów do wymiarów 224x224.

---

## **4. Cel projektu**
Model ma za zadanie wykryć czy obraz przedstawia guz łagodny czy złośliwy. Klasyfikatory oraz sieci neuronowe mogą być dodatkowym narzędziem diagnostycznym. 
---

## **5. Struktura projektu**
Projekt składa się z czterech głównych etapów, każdy w osobnym notatniku `.ipynb`:

| Etap | Nazwa pliku | Opis |
|------|--------------|------|
| 1 | `1_EDA.ipynb` | Analiza danych, wizualizacje, wnioski |
| 2 | `2_Preprocessing_Features.ipynb` | Czyszczenie danych, preprocessing, inżynieria cech |
| 3 | `3_Models_Training.ipynb` | Trening modeli klasycznego ML, sieci neuronowej i transformera |
| 4 | `4_Evaluation.ipynb` | Ewaluacja, porównanie modeli, wizualizacje wyników |

---

## **6. Modele**
Projekt obejmuje trzy różne podejścia do modelowania danych:

### **6.1 Model klasyczny ML**
- Algorytm:  Random Forest
- Krótki opis działania: z obrazu wyodrębniane są cechy np. kolor, tekstura etc, każde drzewo decyzyjne w lesie uczy się na losowo wybranym podzbiorze, po czym klasyfikuje fragment obrazu, a ostateczna decyzja podejmowana jest na podstawie głosowania większościowego wszystkich drzew. 
- Wyniki / metryki:  Accuracy dla PCA 0.405, accuracy dla Radiomics 0.619, Precyzja dla PCA 0.384, Recall dla PCA 0.93, F1 dla PCA 0.543, precyzja, recall oraz f1 dla podejścia cech radiomics wszystkie równe 0, co świadczy o niewystarczającej ilości cech aby model mógł się nauczyć złożoności obrazu mammograficznego

### **6.2 Sieć neuronowa zbudowana od zera**
- Architektura:  CNN
- Liczba warstw / neuronów: dwie warstwy konwoluncyjne (w obu liczba filtrów 16), max pooling, warstwa FC fully connected
- Funkcje aktywacji i optymalizator:  funkcja aktywacji ReLU, funkcja straty CrossEntropyLoss, optymalizator Adam
- Wyniki:  Accuracy 0.583, Precyzja 0.38, Recall 0.148, F1 0.214

### **6.3 Model transformerowy (fine-tuning)**
- Nazwa modelu:  ViT
- Zastosowana biblioteka: Torch 
- Zakres dostosowania:  normalizacja i wagi ImageNet, funkcja straty CrossEntropyLoss z optymalizatorem Adam
- Wyniki:  Accuracy 0.634, Precyzja 0.568, Recall 0.164, F1 0.255

---

## **7. Ewaluacja**
**Użyte metryki:**  
*Accuracy, precision, recall, F1*  

**Porównanie modeli:**
Z racji zerowych wyników dla precyzji, recall i f1 dla podejścia rf_rad, poniżej przedstawiono metryki dla podejścia z wykorzystaniem PCA w Random Forest
| Model | Metryka główna | Wynik | Uwagi |
|--------|----------------|--------|--------|
| Klasyczny ML | Accuracy  | 0.405 | Bardzo wysoki recall 92.9 kosztem skuteczności |
| Sieć neuronowa | Accuracy | 0.583 |  |
| Transformer | Accuracy | 0.634 | Najwyższy ROC-AUC 0.617 |

---

## **8. Wnioski i podsumowanie**
- Który model okazał się najlepszy i dlaczego?
Najlepszy okazał się transformer, ponieważ uzyskał najwyższe accuracy przy jednoczesnym kompromisie między precision i recall, najlepiej nauczył się rozpoznawać wzorce charakterystyczne dla zmian nowotworowych
- Jakie trudności pojawiły się podczas pracy?
Dla modelu na cechach radiomicznych same proste cechy strukturalne nie są wystarczające aby model nauczył się skutecznej klasyfikacji. Niejednorodność danych obrazowych była dużym problemem, różnica w tłach, w skali oraz orientacji obrazu, klasy były niezbalansowane. Jednocześnie obrazy dotyczyły wychwycenia różnic między guzem łagodnym a złośliwym, jest to cięże do nauczenia modelu niż sama detekcja guza/jego braku. 
- Co można by poprawić w przyszłości?
Można wytworzyć więcej cech radiomicznych oraz skorzystać z automatycznej ekstracji PyRadiomics oraz skupić się na zaawansowanej augmentacji danych i różnych symulacjach. W przypadku Random Forest można byłoby wykorzystać siatkę do przeszukiwania hiperparametrów, najpierw w formie random search a następnie grid search na zawężonych zakresach. Finalnie można byłoby również spróbować ensamble'u modelu CNN i VIT oraz uśrednić ich predykcję.
- Jakie potencjalne zastosowania ma ten projekt?
Projekt mógłby pomóc radiologom w analizie obrazów mammograficznych i pełnić funkcję pomocy diagnostycznej. Innym zastosowaniem mogłoby być wsparcie w regionach o ograniczonym dostepie do specjalistów oraz priorytetyzacja badań o największym ryzyku.

---

## **9. Struktura repozytorium**
```
projekt_zum_2025/
│
├── data/
│ ├── train/
│ └── valid/
│ └── test/
├── notebooks/
│ ├── 1_EDA.ipynb
│ ├── 2_Preprocessing_Features.ipynb
│ ├── 3_Models_Training.ipynb
│ └── 4_Evaluation.ipynb
├── models/
├── README.md
└── requirements.txt
```
## **10. Technologia i biblioteki**
- Python 3.10.19
- NumPy, Pandas, Matplotlib, Plotly, Seaborn  
- scikit-learn, 
- PyTorch  

---

## **11. Licencja projektu**
Projekt udostępniony na licencji:  
*(np. MIT License, CC-BY 4.0, GPL-3.0)*  

Źródło danych: zgodnie z licencją wskazaną w sekcji **Dane**.

