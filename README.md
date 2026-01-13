# **Projekt zaliczeniowy – Zastosowania Uczenia Maszynowego**

## **1. Informacje ogólne**
**Nazwa projektu:**  
*Detekcja raka piersi*  

**Autor:**  
Zuzanna Juszczak  

**Kierunek, rok i tryb studiów:**  
*Informatyka, semestr III, studia internetowe*  

**Data oddania projektu:**  
14.01.2026 

---

## **2. Opis projektu**
*Celem projekty jest sklasyfikowanie obrazów mammograficznych jako łagodne lub złośliwe, wykorzystując trzy różne podejścia. Pierwszym podejściem jest klasyczny algorytm uczenia maszynowego oparty na ekstrakcji cech z obrazów. Wykorzystano PCA, radiomics oraz mix obu podejść, następnie trenowano dane przy użyciu Random Forest. Drugim podejściem jest zaimplementowanie sieci CNN. Trzecie podejście obejmuje model ViT aby wykorzystać nowe techniki głębokiego uczenia i sprawdzić czy osiągają wyższą dokładność. *
---

## **3. Dane**
**Źródło danych:**  
*Kaggle*  

**Link do danych:**  
`[https://...](https://www.kaggle.com/datasets/hayder17/breast-cancer-detection/data)`  

**Opis danych:**  
- liczba próbek:  3383
- format danych:  obraz mammograficzny
- rodzaj etykiet / klas:  0 - benign, 1 - malignant
- licencja:  https://opendatacommons.org/licenses/dbcl/1-0/

**Uwagi:**  
Dane zostały przeprocesowane do odpowiednich formatów względem każdego z algorytmów. Dla Random Forest dane przeszły redukcję wymiarowości, dla CNN oraz ViT zostały zmienione wielkości obrazów odpowiednio do wymiarów 128x128 oraz 224x224.

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
- Krótki opis działania:  
- Wyniki / metryki:  

### **6.2 Sieć neuronowa zbudowana od zera**
- Architektura:  CNN
- Liczba warstw / neuronów:  
- Funkcje aktywacji i optymalizator:  
- Wyniki:  

### **6.3 Model transformerowy (fine-tuning)**
- Nazwa modelu:  ViT
- Zastosowana biblioteka: Torch 
- Zakres dostosowania:  
- Wyniki:  

---

## **7. Ewaluacja**
**Użyte metryki:**  
*(np. accuracy, precision, recall, F1, ROC-AUC, MSE itp.)*  

**Porównanie modeli:**

| Model | Metryka główna | Wynik | Uwagi |
|--------|----------------|--------|--------|
| Klasyczny ML |  |  |  |
| Sieć neuronowa |  |  |  |
| Transformer |  |  |  |

**Wizualizacje:**  
- Macierz pomyłek  
- Krzywa ROC  
- Learning curve  

---

## **8. Wnioski i podsumowanie**
- Który model okazał się najlepszy i dlaczego?  
- Jakie trudności pojawiły się podczas pracy?  
- Co można by poprawić w przyszłości?  
- Jakie potencjalne zastosowania ma ten projekt?  

---

## **9. Struktura repozytorium**
```
projekt_zum_2025/
│
├── data/
│ ├── raw/
│ └── processed/
├── notebooks/
│ ├── 1_EDA.ipynb
│ ├── 2_Preprocessing_Features.ipynb
│ ├── 3_Models_Training.ipynb
│ └── 4_Evaluation.ipynb
├── models/
├── results/
├── README.md
└── requirements.txt
```
## **10. Technologia i biblioteki**
- Python 3.x  
- NumPy, Pandas, Matplotlib, Plotly, Seaborn  
- scikit-learn  
- TensorFlow lub PyTorch  
- HuggingFace Transformers  

---

## **11. Licencja projektu**
Projekt udostępniony na licencji:  
*(np. MIT License, CC-BY 4.0, GPL-3.0)*  

Źródło danych: zgodnie z licencją wskazaną w sekcji **Dane**.

